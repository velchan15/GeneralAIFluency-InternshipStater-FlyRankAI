# Prompting Fundamentals on Real Tasks

**Evelyn Anastasia · General AI Fluency · FL-02**
**Task used (from FL-01 audit, target task #9):** Coding sensor integration into ESP32 — PureStream project, pH-4502C sensor.

---

## Baseline (naive prompt)

**Prompt:**
> "Bikinin kode ESP32 buat sensor pH"

**Output:**
```cpp
const int phPin = 34;
void setup() {
  Serial.begin(115200);
}
void loop() {
  int value = analogRead(phPin);
  float ph = value * (14.0 / 4095.0);
  Serial.println(ph);
  delay(1000);
}
```
Generic code — no calibration, no cloud/WiFi, the pH formula is a rough linear guess almost certainly inaccurate for a real sensor.

---

## Version 1 — added: Role Assignment

**Prompt:**
> "Kamu adalah embedded systems engineer berpengalaman yang spesialisasi di kalibrasi sensor analog. Bikinin kode ESP32 buat sensor pH."

**Output:**
```cpp
const int phPin = 34;
float calibration_slope = -0.18;   // TODO: hitung dari 2 titik kalibrasi
float calibration_offset = 7.0;    // TODO: sesuaikan dari hasil kalibrasi

void setup() {
  Serial.begin(115200);
}
void loop() {
  int raw = analogRead(phPin);
  float voltage = raw * (3.3 / 4095.0);
  float ph = calibration_slope * voltage + calibration_offset;
  Serial.println(ph);
  delay(1000);
}
```

**Notes:**
- **What changed in the prompt:** added the role "embedded systems engineer specializing in sensor calibration."
- **What actually improved in the output:** the code now explicitly flags that 2-point calibration is required — went from a careless linear formula to one with clearly marked placeholders for real calibration values.
- **What still failed:** no instructions on *how* to calibrate, just TODO comments.
- **What I'd try next:** give project context so the model understands why accuracy matters here.

---

## Version 2 — added: Context and Motivation

**Prompt:**
> (same as V1) + "Ini buat proyek PureStream — alat monitoring air minum rumah tangga, karena keluarga saya sempat sakit perut akibat air yang nggak dicek kualitasnya. Akurasi penting karena hasil ini dipakai buat notifikasi otomatis kalau air nggak aman, mengacu ke standar WHO/Permenkes (pH aman: 6.5–8.5)."

**Output:**
```cpp
const int phPin = 34;
float calibration_slope = -0.18;
float calibration_offset = 7.0;

const float PH_MIN_SAFE = 6.5;
const float PH_MAX_SAFE = 8.5;

void setup() {
  Serial.begin(115200);
}

void loop() {
  int raw = analogRead(phPin);
  float voltage = raw * (3.3 / 4095.0);
  float ph = calibration_slope * voltage + calibration_offset;

  Serial.print("pH: "); Serial.println(ph);

  if (ph < PH_MIN_SAFE || ph > PH_MAX_SAFE) {
    Serial.println("PERINGATAN: pH di luar batas aman!");
    // TODO: trigger notifikasi Blynk di sini
  }
  delay(1000);
}
```

**Notes:**
- **What changed:** added project context, motivation, and specific threshold numbers.
- **What actually improved:** a big jump — the code now includes safe-range checking logic that was completely absent before, because the model understood the goal wasn't just "read the sensor" but "raise a warning."
- **What still failed:** Blynk notification still a TODO placeholder; variable naming not yet consistent with the rest of the PureStream codebase.
- **What I'd try next:** give an example of my existing code style so naming stays consistent.

---

## Version 3 — added: Few-Shot Examples

**Prompt:**
> (same as V2) + "Ini contoh gaya kode sensor suhu yang udah saya pakai di proyek yang sama, ikutin gaya penamaan dan struktur ini:"
```cpp
#define TEMP_PIN 4
OneWire oneWire(TEMP_PIN);
DallasTemperature tempSensor(&oneWire);

float readTemperature() {
  tempSensor.requestTemperatures();
  return tempSensor.getTempCByIndex(0);
}
```

**Output:**
```cpp
#define PH_PIN 34
const float PH_MIN_SAFE = 6.5;
const float PH_MAX_SAFE = 8.5;
float phCalibrationSlope = -0.18;
float phCalibrationOffset = 7.0;

float readPH() {
  int raw = analogRead(PH_PIN);
  float voltage = raw * (3.3 / 4095.0);
  return phCalibrationSlope * voltage + phCalibrationOffset;
}

bool isPHSafe(float ph) {
  return (ph >= PH_MIN_SAFE && ph <= PH_MAX_SAFE);
}
```

**Notes:**
- **What changed:** gave an existing code snippet as a style reference.
- **What actually improved:** naming is now consistent (`#define PIN`, `readX()` function style camelCase) — the code now looks like it was written by the same person as the temperature sensor code, not pasted from a random source.
- **What still failed:** still loose function fragments, not yet clear how they fit into `setup()`/`loop()`.
- **What I'd try next:** ask for an explicit output structure.

---

## Version 4 — added: Output Structure

**Prompt:**
> (same as V3) + "Strukturkan sebagai: 1) bagian kalibrasi (komentar step-by-step cara kalibrasi manual), 2) fungsi pembacaan sensor, 3) fungsi cek keamanan, 4) integrasi ke loop() utama."

**Output:**
```cpp
// ===== 1. KALIBRASI =====
// a. Celupkan probe ke buffer pH 7.0, catat voltage.
// b. Celupkan probe ke buffer pH 4.0, catat voltage.
// c. slope = (7.0 - 4.0) / (voltage_pH7 - voltage_pH4)
// d. offset = 7.0 - (slope * voltage_pH7)
#define PH_PIN 34
float phCalibrationSlope = -0.18;
float phCalibrationOffset = 7.0;
const float PH_MIN_SAFE = 6.5;
const float PH_MAX_SAFE = 8.5;

// ===== 2. PEMBACAAN SENSOR =====
float readPH() {
  int raw = analogRead(PH_PIN);
  float voltage = raw * (3.3 / 4095.0);
  return phCalibrationSlope * voltage + phCalibrationOffset;
}

// ===== 3. CEK KEAMANAN =====
bool isPHSafe(float ph) {
  return (ph >= PH_MIN_SAFE && ph <= PH_MAX_SAFE);
}

// ===== 4. INTEGRASI LOOP UTAMA =====
void setup() {
  Serial.begin(115200);
}
void loop() {
  float ph = readPH();
  Serial.print("pH: "); Serial.println(ph);
  if (!isPHSafe(ph)) {
    Serial.println("PERINGATAN: pH di luar batas aman!");
  }
  delay(1000);
}
```

**Notes:**
- **What changed:** requested an explicit 4-section output structure.
- **What actually improved:** most useful version for actually learning, not just getting finished code — now includes step-by-step manual calibration instructions in comments, previously just a "TODO."
- **What still failed:** no WiFi/Blynk connection yet — still local logic only.
- **What I'd try next:** break the WiFi/Blynk integration into small steps.

---

## Version 5 — added: Step Decomposition

**Prompt:**
> (same as V4) + "Sekarang breakdown proses integrasi ke Blynk jadi tahapan kecil: dulu kasih tau saya langkah 1 aja (setup koneksi WiFi), tunggu saya konfirmasi paham, baru lanjut langkah berikutnya."

**Output:**
> **Step 1 — WiFi setup:**
> ```cpp
> #include <WiFi.h>
> const char* ssid = "NAMA_WIFI";
> const char* password = "PASSWORD_WIFI";
>
> void setup() {
>   Serial.begin(115200);
>   WiFi.begin(ssid, password);
>   while (WiFi.status() != WL_CONNECTED) {
>     delay(500);
>     Serial.print(".");
>   }
>   Serial.println("WiFi terhubung!");
> }
> ```
> This just connects to WiFi — no Blynk yet. Upload and confirm you see "WiFi terhubung!" in Serial Monitor before moving to the next step.

**Notes:**
- **What changed:** asked the model to decompose the process into confirmed stages.
- **What actually improved:** good for learning in small, unrushed steps, avoiding overwhelm.
- **What still failed / honest trade-off:** for getting a finished deliverable quickly, this technique is actually **less efficient** than Version 4's single structured block — if the goal is a finished code artifact rather than a guided learning session, step decomposition slows things down rather than helping.
- **What I'd try next:** for the final template, keep V4's clear structure without forcing step-by-step confirmation unless explicitly learning something new.

---

## Final Prompt (reusable template)

```
You are an experienced embedded systems engineer specializing in sensor calibration.

I'm building [project name — e.g. "a real-time water quality monitor on ESP32"].
Context: [why accuracy/reliability matters for this specific use case].

Write code for [specific sensor/component], following this style as reference
for naming and structure:
[paste a snippet of your existing code style]

Structure the output as:
1. Calibration section (with step-by-step comments on how to calibrate manually)
2. Sensor reading function
3. Safety/threshold check function
4. Integration into the main setup()/loop()

Keep it as one complete block unless I ask you to break it into stages.
```

---

## Cross-Model Comparison (final prompt run on Claude vs. ChatGPT)

| Aspect | Claude | ChatGPT |
|---|---|---|
| Calibration accuracy | Uses `slope × voltage + offset` with default values (`-0.18`, `7.0`) that look "ready to use" — risk of being mistaken for real calibrated numbers | Uses a more standard 2-point interpolation from actual pH 7/pH 4 voltages, and explicitly warns "do not rely on the example voltages" |
| Stated assumptions | No upfront assumptions block — jumps straight to code | Opens with an explicit "Assumptions" block (pin, ADC resolution, reference voltage) |
| Noise handling | Single raw ADC read per loop, more prone to fluctuation | Averages 10 ADC samples before use — a standard noise-reduction technique |
| Connecting to project context | Doesn't reference other sensors in the project | Proactively raises Automatic Temperature Compensation, since PureStream also has a DS18B20 and pH readings are temperature-sensitive — an insight I didn't ask for |
| Production-readiness advice | None | Suggests storing calibration constants in ESP32 NVS/Preferences so they survive a reboot |
| Tone | Compact, straight to the code | More verbose, structured with section dividers, extra notes at the end |

**Failure points:**
- **Claude:** the clearest weakness is presenting default calibration values that look valid without a strong-enough warning that they're placeholders — risks a beginner forgetting to recalibrate.
- **ChatGPT:** more verbose than strictly necessary for equivalent functionality, and added an assumptions block that wasn't explicitly requested.

**Honest conclusion:** For this task, ChatGPT was slightly stronger on technical accuracy (correct 2-point calibration math) and proactively surfaced a relevant insight (temperature compensation) that Claude missed. Claude was more concise but carried a higher risk of a "confidently wrong default" — more dangerous for a beginner who might not realize recalibration is required.

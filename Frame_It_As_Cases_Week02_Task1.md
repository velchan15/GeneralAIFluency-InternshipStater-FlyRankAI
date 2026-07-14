# Frame It as Cases
**Evelyn Anastasia General AI Fluency Week 2**

## Voice Card
* direct, personal, curious, grounded, no fluff
* No "passionate," "results-driven," or "dynamic." Short sentences. If a line sounds like generic AI copy, it gets rewritten the way I'd actually say it to a friend.

---

## Case Study: PureStream
### Real-Time Water Quality Monitoring on ESP32

#### The Problem
We use PDAM water at home. We always boil it before drinking—that's just what you do. But three of my siblings, two nieces and nephews, and I still got stomach aches and diarrhea, probably from the water, even after boiling. That was the moment. Boiling doesn't tell you what's actually in the water. No pH, no turbidity, nothing you can see. We were trusting it blindly. So I built something to actually check it—pH, temperature, turbidity in real time, instead of assuming water is safe because it looks clear.

#### What I Did and Decided
* **Hardware:** ESP32, chosen for built-in WiFi. The whole point was real-time monitoring, not local logging, so the device needed to talk to the cloud on its own.
* **Sensors:** DS18B20 for temperature, pH-4502C for pH, and an analog turbidity sensor for clarity. I referenced a paper on real-time water quality monitoring that also recommended ORP and TDS sensors—those were too expensive at the time, so I cut them and kept the three I could afford.
* **Thresholds:** WHO and Permenkes (Indonesian Ministry of Health) standards, so "safe" and "unsafe" weren't guesses—they were tied to actual regulation.
* **Cloud:** Blynk IoT. Continuous monitoring, plus automatic notifications when a reading falls outside the safe range.
* **Wiring** was done on a breadboard.
* **What didn't work:** pH calibration was the hardest part. I assumed the pH-4502C would work out of the box - it doesn't. Before I calibrated it with buffer solutions, it gave nonsense readings: pH 3 for water that should've read around 7, and sometimes readings that barely moved no matter what I tested. Wrong assumption, and it cost me the most time on the whole project. The WiFi connection also wasn't reliable—the ESP32 would sometimes fail to send data to Blynk, or send it late. On top of that, the network was hardcoded: switching WiFi meant re-uploading the code, which made testing anywhere but my own house annoying.

#### What Came of It
Once calibration and connection were fixed, I tested three water types side by side:

| Water source | pH | Turbidity | Temp (°C) | Classification |
| :--- | :--- | :--- | :--- | :--- |
| Refill gallon | 7.5 | 13 | 24.75 | Clear |
| Sealed gallon (Aqua) | 6.7 | 18 | 24.94 | Clear |
| PDAM tap water | 7.1 | 10 | 24.88 | Clear |

All three came back "Clear." By the parameters I measured, our tap water wasn't meaningfully different from bottled water. That's not the result I expected, but it's an honest one. It means the health issues my family had probably weren't caused by pH, temperature, or turbidity - there's likely something else going on, like bacteria or chemical contaminants, that these three sensors can't see. The notification system worked correctly whenever a reading was out of range, but since every sample tested safe, I never saw it fire on genuinely bad water.

#### What I'd Do Differently
I'd add a sensor for bacteria or microbiological contamination—the real gap this test exposed—plus the ORP and TDS sensors from my original reference paper, which I skipped early on for cost. For the WiFi problem, I'd switch to something like WiFiManager, so the device can join a new network without re-flashing the code. PureStream is done for now. Next, I'm moving into my undergraduate thesis: a hybrid adaptive Push-to-Talk system that uses machine learning to switch automatically between PoC and conventional radio, based on predicted cellular signal quality.

---

## Bio (About/Homepage)
My family got sick from water we boiled but never checked. So I built PureStream, a real-time ESP32 monitoring system, to find out what boiling doesn't catch. That's the instinct I want to bring into R&D—see a real problem, build the fix. Want to get in touch? Download my CV below.

---

## Before/After - Editing Out Generic AI Copy

**Before (generic AI line):**
> "I am a passionate and results-driven Telecommunication Systems student with a strong interest in IoT technology. dedicated to leveraging innovative solutions to solve real-world problems."

**After (edited, in my voice):**
> "My family got sick from water we boiled but never checked. So I built PureStream, a real-time ESP32 monitoring system, to find out what boiling doesn't catch."

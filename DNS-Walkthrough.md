# DNS Walkthrough — How My Site's Address Will Work

**Evelyn Anastasia · General AI Fluency, PF-04**

---

## What a CNAME record is

A CNAME record is a line in a domain's DNS settings that says "this address is really just another name for that address." Instead of pointing my subdomain (`evelyn.flyrank.ai`, once it's provisioned) directly at a server's raw IP address, a CNAME points it at my hosting provider's own domain (for example, `anstevelynnn.web.app` or `evelyn.netlify.app`). That way, if my host ever changes the server behind the scenes, I don't have to update anything — the CNAME just keeps pointing at the same hostname, and that hostname's own DNS records handle the rest.

## What value mine will hold

Once FlyRank Ops provisions `evelyn.flyrank.ai`, the CNAME record for that subdomain will hold the value of my hosting provider's domain — the exact free URL I'm using now (e.g. `anstevelynnn.web.app`). That's the "answer" the record gives whenever someone looks up my subdomain: "go check that address instead."

## What actually happens when someone types my address

Say someone types `evelyn.flyrank.ai` into their browser. Here's the chain of events, step by step:

1. **The browser asks a resolver.** A resolver is usually run by the person's internet provider or a public service like Google's (8.8.8.8). It's the middleman whose job is to go find the answer to "where does this address live?"

2. **The resolver asks the nameservers.** Nameservers are the authoritative source of truth for a domain — in this case, whoever manages DNS for `flyrank.ai`. The resolver asks them: "what record do you have for `evelyn.flyrank.ai`?"

3. **The nameserver returns the record.** It finds the CNAME record Ops created, which says `evelyn.flyrank.ai` → `anstevelynnn.web.app` (or whatever my host URL is at the time).

4. **The resolver follows the chain one more step.** Since a CNAME just points to another hostname, the resolver now has to look up *that* hostname too, to get its actual IP address. It repeats roughly the same process (asking nameservers) until it gets a real IP address back.

5. **The resolver sends the final answer back to the browser** — the IP address of the server that's actually hosting my site.

6. **The browser connects to that IP address and requests my page.** The hosting provider's server receives the request and sends back my site's files. The browser renders them, and the person sees my portfolio — all of this happening in a fraction of a second, invisibly.

## Why I'm writing this before I need it

Right now there's no subdomain to point anywhere yet — that comes at capstone approval. But when it lands, all I'll need to do is: add the custom domain in my hosting provider's settings, confirm the CNAME value matches what Ops set up, and wait for it to propagate (which just means: wait for resolvers around the world to notice the new record and start using it, since they cache old answers for a while). This document is the checklist I'll follow at that point — nothing about my actual site changes, only how people find their way to it.

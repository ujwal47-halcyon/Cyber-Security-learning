# Day 1 - OSI Model

Date: January 10, 2026
=> Goal:Understand what the OSI model is and why each layer exists.

---
# What is the OSI Model?

- OSI stands for Open Systems Interconnection. It's a framework that breaks down
how data moves across a network into 7 separate layers. Each layer has its own job.

- Example: It like sending a letter, you write it, seal it, address it, hand
it to the post office, it gets sorted, transported, and delivered. Each step is
handled by someone different. OSI is the same idea but for network data.

---
# The 7 Layers:

| Layer | Name         | What it actually does                        |
|-------|--------------|----------------------------------------------|
| 7     | Application  | What the user sees — HTTP, DNS, FTP          |
| 6     | Presentation | Formats, encrypts, compresses data           |
| 5     | Session      | Opens and closes connections between devices |
| 4     | Transport    | TCP (reliable) vs UDP (fast, no guarantee)   |
| 3     | Network      | IP addressing and routing                    |
| 2     | Data Link    | MAC addresses, frames                        |
| 1     | Physical     | Actual cables, signals, bits                 |

---
# Question I Had:

=> Why not just one layer instead of seven?

- Because isolating each function makes troubleshooting easier. If a packet isn't
arriving, you check layer 3. If encryption is broken, you look at layer 6.
Without layers you would be guessing across the entire stack every time something
breaks. So being it as layers is important.

---
# Real-World Trace — Opening a Website

- Typing a URL and hitting Enter triggers all 7 layers:

1. Browser builds an HTTP request                   => (Layer 7)
2. Data gets formatted/encrypted via TLS            => (Layer 6)
3. Session with the server is established           => (Layer 5)
4. TCP breaks data into segments, handles delivery  => (Layer 4)
5. IP routes packets toward the destination         => (Layer 3)
6. Frames are built with MAC addresses              => (Layer 2)
7. Bits travel as electrical/wireless signals       => (Layer 1)


# What I Actually Took Away(Learning Outcome)

- The OSI model is not  something you memorize once and forget. In pentesting,
knowing which layer you're operating on tells you what tools to use and what
can go wrong. ARP spoofing is Layer 2. IP spoofing is Layer 3. Most web attacks
live at Layer 7. That framing matters.
 

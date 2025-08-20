# 📹 Technical Interview Project – Hinglish Guide (Internship Friendly)

Yeh document tumhe apne pehle interview me project explain karne me help karega. Simple Hindi + English (Hinglish) style me likha hai. Practice kar lo 2–3 baar.

---
## 1. 15-Second Pitch (Ultra Short)
“Mera project ek real-time video interview platform hai jahan interviewer aur candidate same room me video call + coding question + feedback ek jagah pe handle kar sakte hain.”

## 2. 30-Second Pitch
“Mainne ek web app banaya hai jisme interviewer aur candidate login karte hain, video call join karte hain, coding problem dekhte hain, multi-language starter code ke saath solve karte hain, aur end me interviewer rating + comments de sakta hai. Sab kuch real‑time update hota hai bina refresh ke.”

## 3. 60-Second Pitch (Thoda Detail)
“Is app me teen core cheezein hain: (1) Secure login Clerk se. (2) Live video + participants Stream SDK se. (3) Real‑time data like interview schedule, comments Convex se. Coding question panel me problem description, examples, constraints aur Monaco Editor hai jise VS Code jaisa feel milta hai. Interview end hone ke baad interviewer star rating + feedback add karta hai jo turant sabko dikhta hai.”

---
## 4. Problem → Solution (Hinglish)
| Problem | Solution |
|---------|----------|
| Alag alag tools (Zoom, Google Doc, Sheet for feedback) me time waste | Sab ek UI me combine kiya |
| Manual refresh / delays | Convex + Stream se instant updates |
| Coding question context missing | Built‑in curated questions with examples |
| Feedback scattered | Structured comments + star rating |

---
## 5. Tech Stack Simple Explanation
| Tech | Simple Reason (Hinglish) |
|------|--------------------------|
| Next.js | Fast React framework + routing ready |
| Clerk | Login / signup ready-made, khud se auth banana nahi pada |
| Stream Video | WebRTC implement karne ka jhanjhat nahi, ready SDK |
| Convex | Backend + real-time database bina REST APIs likhe |
| Tailwind + Radix | Quick styling + accessible components |
| Monaco Editor | VS Code wala experience browser me |

---
## 6. Data Model (Very Simple)
- users: naam, email, image, role (candidate/interviewer), clerkId
- interviews: title, times, status, streamCallId, candidate, interviewer list
- comments: interviewId, rating (1–5), content, interviewerId

Bas 3 main tables. Easy to explain.

---
## 7. Flow (Story Form)
1. User login karta hai → Clerk se ID milti hai.
2. Pehli baar aaya toh Convex me `syncUser` se entry ban jaati hai.
3. Interview schedule create hota hai (interviews table row).
4. Interview time → dono meeting page open karte hain.
5. Stream client token leke video call join karta hai.
6. UI split: left video, right coding panel (resizable).
7. End ke baad interviewer feedback dialog open karta hai → comment + rating save.
8. Comments instantly appear (real-time query re-run).

---
## 8. Important Files (Point Kar Sakte Ho)
| Feature | File |
|---------|------|
| Schema | `convex/schema.ts` |
| Create Interview | `convex/interviews.ts` (`createInterview`) |
| Status Update | `convex/interviews.ts` (`updateInterviewStatus`) |
| Add Comment | `convex/comments.ts` (`addComment`) |
| User Sync | `convex/users.ts` (`syncUser`) |
| Video Room UI | `src/components/MeetingRoom.tsx` |
| Coding Panel | `src/components/CodeEditor.tsx` |
| Feedback Dialog | `src/components/CommentDialog.tsx` |
| Stream Setup | `src/components/providers/StreamClientProvider.tsx` |

---
## 9. Demo Script (Practice Isko Bolke)
1. “Login karta hoon – Clerk manage karta hai authentication.”
2. “Yeh dashboard real-time interviews list show kar raha hai.”
3. “Meeting enter karte hi Stream video layout load ho gaya.”
4. “Main layout Grid/Speaker switch kar sakta hoon.”
5. “Right side coding question: description, examples, constraints.”
6. “Language switch karta hoon – JavaScript / Python / Java starter code update ho jata hai.”
7. “End interview → feedback dialog open → rating + comment add.”
8. “Comment turant appear – real-time by Convex.”
9. “Aage enhance karunga: code persistence + collaborative editing + auto test runner.”

---
## 10. Common Interviewer Questions (Hinglish Answers)
Q1: Real-time kaise achieve hua?  
A: Stream video ke liye, Convex reactive queries data ke liye. Query automatic re-run jab backend me change hota hai.

Q2: Agar code persist karna ho toh?  
A: Ek `solutions` table banata: interviewId, userId, language, code, updatedAt. Editor ke onChange pe debounce karke mutation call.

Q3: Security kya kiya?  
A: Sab mutations me identity check. Stream secret client pe nahi – token provider server side. Public env vars NEXT_PUBLIC prefix.

Q4: Why Convex instead of custom Express API?  
A: Faster prototype, less boilerplate, built-in live subscriptions, type safety.

Q5: Scaling?  
A: Stream handles media infra. Convex horizontally scale hota hai. Frontend static/edge deliver ho sakta hai.

Q6: Future improvement sabse pehle kya?  
A: Code persistence + examiner analytics (average rating, pass rate).

Q7: Trade-off of using Monaco?  
A: Powerful but heavier bundle; acceptable because interview page is focused.

Q8: Failover plan agar Stream down?  
A: Basic fallback text chat + reconnect attempt; (future: alternate provider abstraction).

---
## 11. Simple Diagram (Memory Aid)
```
[User Browser]
  |  Clerk Auth
  v
[Next.js + Providers] --(queries/mutations)--> [Convex]
       |\
       | token
       v
   [Stream Video]
```

---
## 12. Future Ideas (Short Bullets)
- Collaborative cursor + live code
- Code execution sandbox + test cases pass/fail
- Email/calendar invites
- Recording + playback
- AI hint generation (optional)

---
## 13. Words / Phrases To Use (Sound Clear & Confident)
- “Lightweight architecture”
- “Only three core data entities”
- “Token provider pattern for security”
- “Real-time reactivity without manual polling”
- “Extensible foundation”

---
## 14. Avoid These Pitfalls
| Pitfall | Fix |
|---------|-----|
| Over-explaining low-level WebRTC | Bas itna bolo: Stream SDK abstracts signaling & media |
| Forgetting data model | 3 tables yaad rakho |
| Saying “I don’t know” abruptly | Add: “I’d explore X approach” |
| Speaking too fast | Short pauses after key points |

---
## 15. If You Get Stuck
Line to use: “Main exact number yaad nahi, but approach yeh hoga…” then describe steps.

---
## 16. Personal Wrap Line
“Is project ne mujhe real-time systems aur clean minimal data modeling sikhaya. Main ise aage production-grade features tak le jana chahta hoon.”

Good luck! Practice aloud – clarity > complexity. 💪

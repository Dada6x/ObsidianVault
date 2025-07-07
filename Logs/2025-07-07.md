
## ✅ ~={purple}Daily Habits=~
- [ ]  Gym.
- [ ]  LeetCode Proplem.
- [ ]  German.

---

## 🧠 Notes / Reflection

> Write what you built, learned, or struggled with today.

```
What have You done Today ?



What Muscle Group Did You did Today? (if its not rest).



What LeetCode Proplems did You solved Today ?




-------------------------------------------------------------
Something Else :


```


<%*
const today = tp.date.now("MMM D")
const file = await tp.file.find_tfile("📅 2025 Tracker")
if (!file) return
const content = await app.vault.read(file)
const regex = new RegExp(`- \\[ \\] ${today}`, "g")
const updated = content.replace(regex, `- [x] ${today}`)
await app.vault.modify(file, updated)
%>

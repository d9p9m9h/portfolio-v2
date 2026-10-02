## Error chat စတဲ့အခါ သုံးမည့် တိုတောင်းတဲ့စာကြောင်း

ဒါကတော့ chat ထဲမှာ ကူးထည့်ရမည့် **စာကြောင်းတိုလေး** ဖြစ်ပါတယ်။  
ဒါကတော့ တစ်ကြောင်းပဲ ကူးထည့်ရတော့တယ်။

```text
Read docs/ERROR_AGENT.md and docs/ERROR_LOG_TEMPLATE.md. Use them as source of truth. Do not edit files or run commands automatically. I will provide an error intake next.
```

ပြီးရင် အောက်ကလို ဖြည့်ပေးပါ။

```text
Current task or step:
What I was doing:
Command I ran, if any:
Exact error or warning:
Related files:
What I already tried:
Expected result:
```

---

## Context compact ဖြစ်သွားရင် သုံးမည့်စာကြောင်း

အကယ်၍ ကြားထဲမှာ မော်ဒယ်က အစကပေးထားတဲ့ စည်းမျဉ်းတွေ မေ့သွားတယ်လို့ ခံစားရရင် ဒါကို ပို့ပါ။

```text
Context may have been compacted. Re-read docs/ERROR_AGENT.md and docs/ERROR_LOG_TEMPLATE.md before continuing. Do not rely on previous chat memory.
```

ဒါဆိုရင် မော်ဒယ်က **ဖိုင်ထဲက စည်းမျဉ်းကို ပြန်ဖတ်ပြီး** ပြန်ချိတ်နိုင်တယ်။

---

## ဒီနည်းက ဘာကြောင့် ပိုကောင်းလဲ

### အရင်နည်း

```text
Prompt ကို chat အစမှာ ရှည်ကြီးထည့်
→ နောက်ပိုင်းမှာ context တွေများလာ
→ model က compact လုပ်
→ အစကစည်းမျဉ်း မေ့သွားနိုင်
```

### အခုနည်း

```text
စည်းမျဉ်းကို project ဖိုင်ထဲထား
→ လိုရင် ပြန်ဖတ်ခိုင်း
→ မေ့ရင် ပြန်ဖတ်ခိုင်း
→ တစ်ကြောင်းနဲ့ ပြန်ချိတ်နိုင်
→ source of truth က chat ထဲမှာမဟုတ်ဘဲ ဖိုင်ထဲမှာ ရှိ
```

ဒါက **context window limitation** အတွက် အရမ်းအသုံးဝင်တယ်။

---

## အသုံးပြုတဲ့အခါ အကြံပြုချက်များ

### တစ်ခုချင်းစီသော အမှားအတွက် သီးသန့်မှတ်တမ်းထားပါ

တူညီတဲ့ root cause ကို တစ်ခုတည်း မှတ်တမ်းတင်ပါ။  
မတူညီတဲ့ အမှားတွေကို မှတ်တမ်းခွဲပါ။

---

### ပြင်ဆင်ပြီးမှ `status: solved` လုပ်ပါ

အမှားကို စမ်းသပ်ပြီးမှ —

```yaml
status: solved
```

လို့ ပြောင်းပါ။

မစမ်းရသေးရင် —

```yaml
status: open
```

ထားပါ။

---

### မှတ်တမ်းတစ်ခုချင်းစီကို နာမည်ပေးတဲ့အခါ

```text
ERR-YYYYMMDD-HHMM-short-title.md
```

ပုံစံကို သုံးပါ။

ဥပမာ —

```text
ERR-20260622-1430-tailwind-import-failed.md
```

---

### Obsidian ထဲမှာ သိမ်းမည့်နေရာ

အကြံပြုထားတဲ့နေရာ —

```text
Vault/
└── 90 Error History/
    └── flimmaker-portfolio/
```

---

## အတိုချုပ်

အခုလိုလုပ်ထားရင် —

```text
GLM 5.3 Flash က context compact လုပ်လည်း
ဖိုင်ထဲက စည်းမျဉ်းကို ပြန်ဖတ်ခိုင်းနိုင်တယ်
```

```text
အမှားတစ်ခုချင်းစီကို
ဘယ်အဆင့်မှာဖြစ်ခဲ့တယ်
ဘာအမျိုးအစားလဲ
ဘာကြောင့်ဖြစ်တယ်
ဘယ်လိုပြင်ရတယ်
နောက်တစ်ခါ ဘယ်လိုကာကွယ်မလဲ
ဆိုတာ မှတ်တမ်းတင်နိုင်တယ်
```

```text
chat history ပေါ် မမှီခိုဘဲ
project files ပေါ်မှာ မူတည်တဲ့
တည်ငြိမ်တဲ့ error learning system ဖြစ်သွားတယ်
```
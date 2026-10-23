# srtsplit Deployment

## 1. Telegram token ကို အသစ်ပြောင်းပါ

အရင် repository ထဲမှာ token public ဖြစ်နေသောကြောင့် @BotFather မှာ token ကို revoke လုပ်ပြီး အသစ် generate လုပ်ပါ။ Token ကို GitHub code ထဲ မထည့်ပါနှင့်။

## 2. Hosting environment variables

ထည့်ရန် required variable:

```text
BOT_TOKEN=<BotFather ကရသော token အသစ်>
```

ရွေးချယ်နိုင်သော variables:

```text
MAX_FILE_SIZE=20971520
MAX_PEOPLE=100
DROP_PENDING_UPDATES=false
```

## 3. Render

Telegram polling အတွက် **Background Worker** service သုံးပါ။ Build command:

```text
pip install -r requirements.txt
```

Start command:

```text
python main.py
```

`Procfile` ကိုအသုံးပြုလျှင် `worker: python main.py` ဖြစ်ပါသည်။ Render/Railway/Koyeb ထဲမှ bot instance တစ်ခုတည်းကိုသာ run ထားပါ။

## 4. စစ်ဆေးရန် logs

အောင်မြင်သော startup log တွင် အောက်ပါစာကြောင်းများ ပေါ်ရပါမည်:

```text
Starting health server
Webhook cleared; polling is ready
Starting Telegram polling
```

ဖိုင်ပို့ပြီးနောက်:

```text
Document received
Telegram file info received
Download completed
Counting completed
Reply sent successfully
```

`terminated by other getUpdates request` ပေါ်ပါက token သုံးနေသော deployment/process တစ်ခုထက်ပိုနေပါသည်။ အခြား deployment များကိုပိတ်ပြီး token အသစ်ဖြင့် တစ်နေရာတည်း run ပါ။

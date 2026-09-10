import streamlit as st

# تنظیمات صفحه
st.set_page_config(page_title="مخصوص علی ❤️", page_icon="💖", layout="centered")

# استایل‌های CSS - طراحی شیک و غیرخشک
st.markdown(
    """
    <style>
    .stApp { background: linear-gradient(135deg, #fdfcfb 0%, #e2d1c3 100%); }
    h1, h2 { color: #5d4037 !important; text-align: center; font-family: 'Tahoma', sans-serif; }
    .stButton > button {
        background: #8d6e63; color: white; border: none; border-radius: 20px;
        padding: 0.6rem 2rem; font-weight: bold; margin: 0.5rem;
    }
    .stButton > button:hover { background: #6d4c41; }
    .main-container {
        background: rgba(255, 255, 255, 0.9); padding: 2rem; border-radius: 25px;
        box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    }
    .input-box { border: 2px solid #d7ccc8 !important; border-radius: 15px !important; }
    .heart { font-size: 60px; text-align: center; animation: heartbeat 1.5s infinite; }
    @keyframes heartbeat { 0% { transform: scale(1); } 50% { transform: scale(1.2); } 100% { transform: scale(1); } }
    </style>
    """,
    unsafe_allow_html=True,
)

# متن‌های ثابت (بدون تغییر)
INTRO_TEXT = """علی عزیزم،
تنها عشق زندگی من، من با یه رونمایی دیگه از عشقم نسبت بهت آمادم.
ازت می‌خوام هیچ‌وقت هر اتفاقی بین من و تو افتاد به عشقی که نسبت بهت دارم توهین نکنی.
تو تنها پسر ایده‌آل منی، تنها پسری هستی که از نظرم همه‌چی‌تمومه.
برای همین بودنت تو زندگیم، مثل آبی که تو کویر پیدا می‌شه، مثل لبخندی که لابه‌لای اشک‌های بی‌وقفه پیداش می‌شه، مثل امیدی که تو اوج ناامیدی بهش پناه می‌بریم، مثل نوری که تو اوج تاریکی چشمک می‌زنه.
بودنت تو زندگیم ارزشمنده. تنهام نذار (از طرف عشق دل‌بسته‌ات یکتا).
تقدیم با عشق، دوست دارم.
اگه آماده‌ای بریم ادامه کار! 😂♥️💫"""

FINALE_TEXT = """علی جانم، همه سوال‌ها رو پشت سر گذاشتیم... 🌹💖
اما می‌دونی؟ جواب هر کدوم از این‌ها فقط یه بهانه بود تا بهت بگم چقدر بودنت برام حیات‌بخشه.
تو فقط یه عشق نیستی، تو دلیل بیداری‌هام، دلیل لبخندهای بی‌دلیلم و قشنگ‌ترین اتفاق عمرمی.
این قلب من، این احساس من، تا ابد مال توئه.
قول بده که همیشه همین‌طور مهربون و عالی بمونی، چون من بدون تو، مثل یه کتاب بی‌پایانم که هیچ‌وقت به خط آخر نمی‌رسه.
دوستت دارم، بی‌نهایت و تا همیشه! 💘✨"""

# لیست ۳۰ سوال جدید، دلبرانه و شیک
QUESTIONS = [
    {"q": "اولین چیزی که با دیدنم تو ذهنت اومد چی بود؟", "yeah": "همون چیزی که قلبم می‌خواست ❤️", "no": "خب، زودتر بهم بگو چی بود! 😉"},
    {"q": "به نظرت ما تو یه دنیای موازی هم مال همیم؟", "yeah": "توی تمام دنیاها مال همیم ♾️", "no": "توی این دنیا که حتماً هستیم 🥰"},
    {"q": "وقتی می‌خندم، دنیات قشنگ‌تر می‌شه؟", "yeah": "دنیام با خنده‌هات ساخته می‌شه 😍", "no": "پس قول بده فقط بخندونی‌ام 🥺"},
    {"q": "به نظرت چشمای من، قشنگ‌ترین جای دنیا نیست؟", "yeah": "چشمات دریای آرامش منه 🌊", "no": "پس چیه؟ بگو تا بدونم! 🤔"},
    {"q": "حس می‌کنی عشقمون هر روز عمیق‌تر میشه؟", "yeah": "هر روز تازه تر از دیروز 💖", "no": "پس بیاریمش بالا! 🚀"},
    {"q": "اگه بگم همه‌چی‌تمومی، باور می‌کنی؟", "yeah": "با تمام وجودم باور دارم 💫", "no": "چون تو خودِ کمالی برای من 😍"},
    {"q": "دلت می‌خواد الان دستم توی دستت باشه؟", "yeah": "همیشه جاش اونجاست 🤝", "no": "پس بیا تا بگیریش 🌹"},
    {"q": "به نظرت صدات قشنگ‌ترین موسیقیه؟", "yeah": "صدای تو آرامش شب‌های منه 🎶", "no": "پس برام بخون 🎤"},
    {"q": "فکر می‌کنی بدون هم یه روز دوام میاریم؟", "yeah": "هرگز، ما بهم وصلیم 🔗", "no": "خوبیش اینه که لازم نیست امتحان کنیم 😉"},
    {"q": "آرامش یعنی بودنِ من کنارت؟", "yeah": "آرامش یعنی تو 😌", "no": "پس بیا تا بیشتر کنارت باشم 🥰"},
    {"q": "فکر می‌کنی خوش‌شانس‌ترین آدمِ دنیام که دارمت؟", "yeah": "خوش‌شانس‌ترینی 🍀", "no": "من خوش‌شانسم که تو رو دارم 💖"},
    {"q": "اگه بگم دلم برات پر می‌زنه، باورت می‌شه؟", "yeah": "با تمام وجودم 🌹", "no": "دلم که همیشه پیشته، نمی‌بینی؟ 😍"},
    {"q": "به نظرت ما زوجِ ایده‌آلِ قصه‌ها هستیم؟", "yeah": "ما خودِ قصه هستیم 📖", "no": "قصه رو خودمون می‌سازیم ✨"},
    {"q": "فکر می‌کنی از این نزدیک‌تر هم می‌شه به هم بود؟", "yeah": "توی قلب هم هستیم ❤️", "no": "پس بیایم نزدیک‌تر 🫂"},
    {"q": "وقتی بهت فکر می‌کنم، متوجه میشی؟", "yeah": "حس می‌کنم ضربان قلبت رو 💞", "no": "پس باید حواست رو جمع‌تر کنی 😉"},
    {"q": "به نظرت خنده‌هامون با هم، صدای بهشته؟", "yeah": "بهترین آهنگ زندگیه 🎶", "no": "پس بیشتر بخندیم 😆"},
    {"q": "فکر می‌کنی هرچی بگذره، عاشقت‌تر میشم؟", "yeah": "هر ثانیه بیشتر 😍", "no": "مگه می‌شه کمتر بشه؟ 🤔"},
    {"q": "دوست داری همیشه سوپرایزت کنم؟", "yeah": "عاشق سوپرایزهای توام 🎁", "no": "پس آماده باش برای بعدی 😏"},
    {"q": "به نظرت من همون نیمه گمشدتم؟", "yeah": "تو تمامِ منی 🧩", "no": "پیدات کردم دیگه! ❤️"},
    {"q": "حس می‌کنی کنار من، خودِ واقعیت هستی؟", "yeah": "آزاد و رها 🕊️", "no": "بیا تا دوباره کشفش کنیم 🔎"},
    {"q": "به نظرت بوسه‌هات، درمونِ همه دردهامه؟", "yeah": "معجزه می‌کنه 💋", "no": "پس معجزه کن 😉"},
    {"q": "فکر می‌کنی توی شلوغی‌های دنیا، فقط همو می‌بینیم؟", "yeah": "فقط تو 👁️", "no": "چشمت رو باز کن، من همینجام ❤️"},
    {"q": "دوست داری با هم سفر کنیم دورِ دنیا؟", "yeah": "با تو، حتی تا ماه 🚀", "no": "فقط مقصد رو بگو 🌍"},
    {"q": "به نظرت دیوونه‌بازیامون، قشنگ‌ترین خاطره‌س؟", "yeah": "بهترین خاطره‌ها رو ساختیم 😂", "no": "پس بیشتر دیوونه‌بازی کنیم 🤪"},
    {"q": "فکر می‌کنی آینده‌مون چقدر درخشان‌تر از امروزه؟", "yeah": "مثل خورشید ✨", "no": "آینده رو خودمون می‌سازیم 💪"},
    {"q": "به نظرت من بهترین انتخابِ زندگیت بودم؟", "yeah": "بهترینِ بهترین‌ها 💎", "no": "انتخابِ اصلی منی 😉"},
    {"q": "حس می‌کنی روحمون با هم گره خورده؟", "yeah": "یکی شدیم 🧶", "no": "بیا تا محکم‌ترش کنیم 💖"},
    {"q": "دوست داری همیشه با هم چای بنوشیم؟", "yeah": "با تو تلخیشم شیرینه ☕", "no": "قهوه چطور؟ 🤔"},
    {"q": "فکر می‌کنی هرگز از هم خسته نمی‌شیم؟", "yeah": "خستگی تو رابطه‌مون راه نداره 🚫", "no": "ما همیشه تازه‌ایم ✨"},
    {"q": "به نظرت، تو همه دنیای منی؟", "yeah": "تو هم دنیای منی ❤️", "no": "بده بگم که هستی! 🥰"},
]

# مدیریت وضعیت
if "stage" not in st.session_state: st.session_state["stage"] = "input_form"
if "q_index" not in st.session_state: st.session_state["q_index"] = 0
if "last_reaction" not in st.session_state: st.session_state["last_reaction"] = ""
if "last_action" not in st.session_state: st.session_state["last_action"] = ""

st.title("پنل اختصاصی علی عزیز 💖")

# مرحله ۱: فرم ورودی (جدید)
if st.session_state["stage"] == "input_form":
    with st.container():
        st.markdown('<div class="main-container">', unsafe_allow_html=True)
        st.subheader("قبل از ورود به دنیای ما، مشخصاتت رو ثبت کن:")
        ali_name = st.text_input("۱. اسم تنها عشق خود را وارد کنید:")
        date_input = st.text_input("۲. تاریخ شرکت در نظر سنجی:")
        word_for_yekta = st.text_input("۳. یک کلمه که وصف‌کننده زیبایی یکتا:")
        dream_place = st.text_input("۴. مقصد سفر رویاهای مشترکمون کجاست؟:")
        future_promise = st.text_input("۵. یه جمله برای همیشه موندن کنار من بنویس:")
        
        if st.button("تأیید و ورود"):
            if ali_name and date_input and word_for_yekta and dream_place and future_promise:
                st.session_state["stage"] = "intro"
                st.rerun()
            else:
                st.warning("عزیزم همه‌ی فیلدها رو باید پر کنی تا وارد شیم! 💖")
        st.markdown('</div>', unsafe_allow_html=True)

# مرحله ۲: مقدمه
elif st.session_state["stage"] == "intro":
    st.markdown(f'<div class="main-container">{INTRO_TEXT}</div>', unsafe_allow_html=True)
    if st.button("شروع 🌹"):
        st.session_state["stage"] = "questions"
        st.rerun()

# مرحله ۳: سوالات
elif st.session_state["stage"] == "questions":
    idx = st.session_state["q_index"]
    if idx >= len(QUESTIONS):
        st.session_state["stage"] = "finale"
        st.rerun()
    else:
        item = QUESTIONS[idx]
        st.progress((idx + 1) / len(QUESTIONS))
        st.markdown(f'<div class="main-container" style="text-align:center;"><h3>سؤال {idx + 1} از {len(QUESTIONS)} 💌</h3><br><h4>{item["q"]}</h4></div>', unsafe_allow_html=True)
        col1, col2 = st.columns(2)
        with col1:
            if st.button("آره 💕"):
                st.session_state["last_reaction"] = item["yeah"]
                st.session_state["last_action"] = "yes"
                st.session_state["stage"] = "visual_feedback"
                st.rerun()
        with col2:
            if st.button("نه 😜"):
                st.session_state["last_reaction"] = item["no"] + " 😔"
                st.session_state["last_action"] = "no"
                st.session_state["stage"] = "visual_feedback"
                st.rerun()

# مرحله ۴: بازخورد بصری
elif st.session_state["stage"] == "visual_feedback":
    st.markdown('<div class="main-container" style="text-align:center;">', unsafe_allow_html=True)
    if st.session_state["last_action"] == "yes":
        st.markdown('<div class="heart">💖</div>', unsafe_allow_html=True)
    else:
        st.markdown('<div style="font-size:60px; text-align:center;">😔</div>', unsafe_allow_html=True)
    
    st.write(f"### {st.session_state['last_reaction']}")
    
    if st.button("ادامه ➡️"):
        st.session_state["q_index"] += 1
        st.session_state["stage"] = "questions"
        st.rerun()
    st.markdown('</div>', unsafe_allow_html=True)

# مرحله ۵: پایان
elif st.session_state["stage"] == "finale":
    st.markdown(f'<div class="main-container">{FINALE_TEXT}</div>', unsafe_allow_html=True)
    if st.button("دوباره از اول 🔁"):
        st.session_state["stage"] = "input_form"
        st.session_state["q_index"] = 0
        st.rerun()

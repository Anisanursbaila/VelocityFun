import streamlit as st
import random

# Atur halaman
st.set_page_config(page_title="Belajar Kecepatan & Debit", layout="centered")

# Tampilan background sederhana (langit biru - rumput hijau)
st.markdown("""
    <style>
    .stApp {
        background: linear-gradient(to bottom, #87ceeb 0%, #b2fba5 100%);
    }
    </style>
""", unsafe_allow_html=True)

# Navigasi utama
menu = st.sidebar.radio("Navigasi", ["Home", "Materi", "Soal", "Games", "Video Pembelajaran"])

# Halaman Home
if menu == "Home":
    st.title("🌟 Belajar Kecepatan & Debit - SD Kelas 5 🌟")
    st.image("anak_taman.png", caption="Anak-anak bermain di taman", use_column_width=True)
    st.write("Selamat datang di aplikasi pembelajaran interaktif. Silakan pilih menu di samping untuk belajar!")

# Halaman Materi
elif menu == "Materi":
    st.header("📘 Materi Kecepatan & Debit")
    st.subheader("Apa itu Kecepatan?")
    st.write("Kecepatan adalah jarak yang ditempuh tiap satuan waktu. Rumus: **v = s ÷ t**.")

    st.subheader("Apa itu Debit?")
    st.write("Debit adalah volume air yang mengalir tiap satuan waktu. Rumus: **Q = V ÷ t**.")

    st.info("Contoh: Mobil melaju 60 km/jam → dalam 2 jam jarak yang ditempuh 120 km.")

# Halaman Soal
elif menu == "Soal":
    st.header("📝 Kuis Interaktif")
    score = 0

    # 10 Soal Pilihan Ganda
    soal_pg = [
        ("1. 300 m ditempuh 5 menit, berapa kecepatan?", ["45", "60", "75"], "60"),
        ("2. 120 liter air mengalir 2 menit, berapa debit?", ["30", "60", "120"], "60"),
        ("3. Mobil 80 km/jam selama 2 jam, jaraknya?", ["80", "120", "160"], "160"),
        ("4. 500 m ditempuh 10 menit, kecepatan?", ["25", "50", "75"], "50"),
        ("5. Debit 200 L/4 menit = ?", ["25", "40", "50"], "50"),
        ("6. Sepeda 15 km/jam selama 2 jam, jarak?", ["15", "30", "45"], "30"),
        ("7. 600 m ditempuh 5 menit, kecepatan?", ["100", "120", "150"], "120"),
        ("8. 90 liter/3 menit, debit?", ["20", "25", "30"], "30"),
        ("9. Kecepatan 10 m/s dalam 30 s, jarak?", ["200", "250", "300"], "300"),
        ("10. Debit 500 L/10 menit = ?", ["40", "50", "60"], "50"),
    ]

    for q, options, ans in soal_pg:
        jawaban = st.radio(q, options, key=q)
        if jawaban == ans:
            score += 1
            st.success("⭐ Benar!")
        elif jawaban != "":
            st.error("❌ Salah. Coba lagi!")

    # 5 Soal Pasangan (Matching)
    st.subheader("🔗 Soal Pasangan")
    pasangan = {
        "Kecepatan": "Jarak ÷ Waktu",
        "Debit": "Volume ÷ Waktu",
        "Jarak": "Kecepatan × Waktu",
        "Volume": "Debit × Waktu",
        "Waktu": "Jarak ÷ Kecepatan",
    }

    for k, v in pasangan.items():
        jawaban = st.text_input(f"{k} = ...", key=k)
        if jawaban.strip().lower() == v.lower():
            score += 1
            st.success("⭐ Benar!")

    st.write(f"Total Skor kamu: {score} ⭐")

# Halaman Games
elif menu == "Games":
    st.header("🎮 Game Tangkap Bintang")
    st.write("Tebak angka 1-5 untuk menangkap bintang!")

    angka = random.randint(1, 5)
    tebakan = st.number_input("Masukkan angka tebakan (1-5):", min_value=1, max_value=5, step=1)

    if st.button("Tangkap!"):
        if tebakan == angka:
            st.success("⭐ Hebat! Kamu berhasil menangkap bintang!")
        else:
            st.error("❌ Belum berhasil, coba lagi!")

# Halaman Video Pembelajaran
elif menu == "Video Pembelajaran":
    st.header("🎥 Video Pembelajaran")
    st.video("https://www.youtube.com/watch?v=1K0q9xw1g2Y")
    st.video("https://www.youtube.com/watch?v=jfKfPfyJRdk")
    st.video("https://www.youtube.com/watch?v=2vjPBrBU-TM")

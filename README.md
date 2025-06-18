<h1 align="center"> Retrieval-Augmented Generation with Gradio and Groq API Key</h1>
<p align="center"> Natural Language Processing Project</p>

<div align="center">

<img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">

</div>

### Name : Abila Prastika Navilat
### Tech Stack : Python, Gradio, LangChain, HuggingFace Embedding, FAISS vector store

---

### 1. Analysis about how the project works
- TODO
Proyek ini adalah sebuah aplikasi cerdas yang memungkinkan pengguna untuk mengunggah file PDF, lalu mengajukan pertanyaan berdasarkan isi dari file tersebut. Aplikasi ini memanfaatkan teknologi RAG (Retrieval-Augmented Generation), di mana isi dokumen akan diproses dan dipahami terlebih dahulu sebelum digunakan sebagai dasar untuk menjawab pertanyaan.
Begitu pengguna mengunggah file PDF, sistem akan membacanya, memotong isi dokumen menjadi bagian-bagian kecil, lalu menyimpannya dalam bentuk vektor menggunakan model pemrosesan bahasa alami dari HuggingFace. Semua potongan informasi itu disimpan ke dalam basis data vektor (FAISS), agar nanti bisa dicari kembali dengan cepat dan akurat.
Saat pengguna mengetikkan pertanyaan, sistem akan mencari bagian isi dokumen yang paling relevan, lalu mengirimkan bagian tersebut ke model bahasa besar (LLM) dari Groq, seperti model LLaMA atau Mixtral, untuk menghasilkan jawaban yang tepat berdasarkan konteks yang ditemukan.
Aplikasi ini dilengkapi dengan antarmuka pengguna yang simpel berbasis Gradio. Pengguna hanya perlu mengunggah PDF, klik tombol “Proses PDF”, lalu bisa langsung mengajukan pertanyaan. Jawaban akan langsung ditampilkan.
Secara keseluruhan, aplikasi ini sangat berguna untuk memahami isi dokumen panjang, seperti jurnal, laporan, atau buku, hanya dengan bertanya menggunakan bahasa alami.

### 2. Analysis about how different every model works on Retrieval-Augmented Generation

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile", # Change the model in the code
        temperature=0.2
    )
```
- Model used : ```[llama-3.3-70b-versatile, deepseek-r1-distill-llama-70b, gemma2-9b-it]```

2.1 Analysis on ```llama-3.3-70b-versatile``` : 
- TODO
Penggunaan model ini cocok untuk berbagai tugas pemrosesan bahasa alami seperti menjawab pertanyaan, merangkum, menerjemahkan, atau menulis ulang teks dengan lebih alami dan masuk akal. Dalam konteks aplikasi RAG seperti ini, model llama-3.3-70b-versatile sangat membantu untuk menghasilkan jawaban yang lebih relevan dan kontekstual, karena modelnya sudah dilatih dengan data yang luas dan beragam.

2.2 Analysis on ```deepseek-r1-distill-llama-70b``` : 
- TODO
Salah satu model bahasa besar (large language model) yang dikembangkan dengan pendekatan distillation, yaitu proses penyederhanaan dari model yang lebih besar agar tetap mampu memberikan hasil yang baik namun dengan efisiensi yang lebih tinggi. Penggunaan model ini dalam aplikasi RAG sangat cocok karena mampu menangani pertanyaan-pertanyaan kompleks berdasarkan dokumen, namun tetap memiliki performa yang cukup efisien untuk diakses melalui API seperti Groq. Model ini biasanya dipilih ketika pengguna membutuhkan keseimbangan antara akurasi jawaban dan kecepatan respons.

2.3 Analysis on ```gemma2-9b-it``` : 
- TODO
Model ini sudah dilatih secara khusus agar mampu mengikuti perintah atau instruksi dari pengguna dalam format percakapan. Dengan kemampuan ini, gemma2-9b-it sangat cocok digunakan dalam aplikasi seperti chatbot, sistem tanya jawab dokumen, dan asisten virtual, karena dapat memberikan respon yang relevan dan terarah berdasarkan masukan pengguna. Selain itu, model ini juga lebih efisien dan cepat dijalankan, sehingga cocok untuk proyek yang membutuhkan waktu respons singkat namun tetap akurat.

### 3. Analysis about how temperature works

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",
        temperature=0.2 # Change the temperature value here and analzye
    )
```

3.1 Analysis on higher temperature 
- TODO
Jika kamu menggunakan temperature yang tinggi, misalnya 0.9, maka model akan menghasilkan jawaban yang lebih bervariasi, kreatif, dan tidak kaku. Namun, semakin tinggi temperaturnya, semakin besar kemungkinan model memberikan jawaban yang kurang akurat dan imput menjadi tidak konsisten dari pertanyaan ke pertanyaan

3.2 Analysis on lower temperature
- TODO
Dengan temperature rendah seperti 0.2, model akan memberikan jawaban yang lebih serius, fokus, konsisten, logis dan lebih aman. Cocok untuk penggunaan formal, teknis dan faktual.

### 4. How to run the project

- Clone this repository with : 

```git
git clone https://github.com/arifian853/RAG_with_GroqAPI.git
```
- TODO (Done)

- Copy the ```.env.example``` file and rename it to ```.env```

```
GROQ_API_KEY=your-groq-api-key
```
- TODO (Done)

- Fill the ```GROQ_API_KEY``` with your Groq API Key, find it here : https://console.groq.com/keys
- TODO (Done)

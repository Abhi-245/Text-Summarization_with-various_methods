# Text-Summarization_with_various_methods

# 🧠 LangChain-Powered Text Summarization Playground 🚀

Welcome to the magical world of **automated summarization** using **LangChain**, **Python**, and **Groq's LLaMA 3** model! This project is a hands-on dive into summarizing speeches, PDFs, and large documents using multiple cool techniques. 💡

Whether you’re working with a one-page speech or a 100-page book, we’ve got a summarization method for every occasion.

---

## 🛠️ What's Inside?

We explored and implemented **five** main summarization techniques using LangChain:

---

### 🗣️ 1. **Basic Prompt Summarization**

📌 **What it does:** Takes a simple speech and returns a concise summary using plain prompts.

🧪 **Key Tool:** `ChatGroq`, `chat_messages`, and direct LLM call.

🔥 **Why use it?** When the text is short and you want a super quick, precise summary.

---

### 🧾 2. **Prompt Templates for Multilingual Summaries**

📌 **What it does:** Uses `PromptTemplate` to define a reusable prompt that generates summaries in any language (we used **Hindi** 🇮🇳).

🧪 **Key Tool:** `LLMChain` with a parameterized template.

🌍 **Why use it?** When you want flexible, repeatable summarization in multiple languages.

---

### 📄 3. **StuffDocuments Chain**

📌 **What it does:** Reads text from a PDF and summarizes it by stuffing all content into the LLM at once.

🧪 **Key Tool:** `load_summarize_chain(chain_type='stuff')`

📏 **Best For:** Short documents that fit within token limits.

⚠️ **Heads-Up:** Not ideal for large files. You'll hit token limits fast.

---

### 🧩 4. **Map-Reduce Chain**

📌 **What it does:** Splits large documents into chunks (map step), summarizes each, then combines the results into a final summary (reduce step).

🧪 **Key Tool:** `load_summarize_chain(chain_type='map_reduce')` with `RecursiveCharacterTextSplitter`.

⚙️ **Bonus:** You can customize the `map_prompt` and `combine_prompt` to format your final summary with numbered points and a **motivational title** 💪.

💡 **Best For:** Long PDFs, eBooks, or scraped data — handles large context like a champ.

---

### 🔁 5. **Refine Chain**

📌 **What it does:** Starts with an initial summary and *refines* it as it sees new chunks of the document.

🧪 **Key Tool:** `load_summarize_chain(chain_type='refine')`

🧠 **Why use it?** When you want the model to build a progressively improved and *cohesive* summary across many parts.

---

## 📊 Comparison of Summarization Methods

| Method               | Best Use Case                      | Handles Long Docs | Fast? ⚡ | Custom Prompts | Notes |
|----------------------|------------------------------------|-------------------|----------|----------------|-------|
| **Basic Prompt**     | Short speeches or paragraphs       | ❌                | ✅       | ❌             | Quickest setup |
| **PromptTemplate**   | Multi-language / repeated use      | ❌                | ✅       | ✅             | Great for i18n |
| **Stuff Chain**      | Small PDFs or doc pages            | ❌ (≤ 4K tokens)   | ✅       | ✅             | Simple, but limited |
| **Map-Reduce**       | Large PDFs, chapters, reports      | ✅                | ⚠️       | ✅✅            | More control & scalable |
| **Refine Chain**     | When quality & consistency matter  | ✅                | ❌       | ✅             | Slower, but more accurate |

---

## 🧩 Dependencies

Make sure you've got these installed:

```bash
pip install langchain langchain-groq langchain_community groq python-dotenv PyPDF2 transformers

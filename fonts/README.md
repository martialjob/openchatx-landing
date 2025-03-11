# 📜 Font Optimization Guide for PurrrChat

## 🎯 Why Optimize Fonts?
For privacy and performance, we **self-host fonts** instead of using Google Fonts. However, **TTF fonts** are large and not optimized for the web. To ensure fast loading times and compatibility, we convert them to **WOFF** and **WOFF2**.

---

## 📌 Steps to Convert TTF to WOFF/WOFF2

### **1️⃣ Install Font Conversion Tools**
If you're using **Linux/macOS**, install `fonttools` and `brotli`:
```sh
pip install fonttools brotli
```

For **Windows**, install Python and run the above command in PowerShell.

---

### **2️⃣ Convert TTF to WOFF and WOFF2**
Run the following commands inside your **fonts folder**:

```sh
# Convert TTF to WOFF
pyftsubset VT323.ttf --output-file=VT323.woff --flavor=woff --layout-features='*' --drop-tables+=GSUB,GPOS

# Convert TTF to WOFF2
pyftsubset VT323.ttf --output-file=VT323.woff2 --flavor=woff2 --layout-features='*' --drop-tables+=GSUB,GPOS
```

💡 **Alternative:** If you prefer a graphical tool, use an **online converter**:
- [CloudConvert](https://cloudconvert.com/ttf-to-woff2)
- [Transfonter](https://transfonter.org/)

---

### **3️⃣ Update Your CSS to Use the Fonts**
Once the fonts are converted, update your CSS file to use them:

```css
@font-face {
    font-family: 'VT323';
    src: url('fonts/VT323.woff2') format('woff2'),
         url('fonts/VT323.woff') format('woff'),
         url('fonts/VT323.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
}
```

🔹 **WOFF2:** Best for modern browsers (smallest size, fastest loading)
🔹 **WOFF:** Compatible with most browsers (slightly larger than WOFF2)
🔹 **TTF:** Fallback for older browsers (largest file size)

---

### **4️⃣ Organize Your Fonts Folder**
Your project structure should look like this:
```
📂 fonts/
│── VT323.ttf
│── VT323.woff
│── VT323.woff2
```

---

## 🚀 Final Steps
✅ Convert **TTF → WOFF/WOFF2**
✅ Update **CSS with @font-face**
✅ Store fonts in a **`fonts/`** folder
✅ Test loading speed using **[PageSpeed Insights](https://pagespeed.web.dev/)**

Now **PurrrChat is optimized for speed and privacy!** 🐾🔥


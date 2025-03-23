<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Compress your images online with the best image compression tool. Choose compression levels from 1 to 10 and optimize your images for web and mobile.">
  <meta name="keywords" content="image compression, compress images, optimize images, image optimizer, Arnav">
  <meta name="author" content="Arnav">
  <title>World's Best Image Compression Tool | Compressify</title>
  <!-- Google AdSense -->
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_AD_CLIENT_ID" crossorigin="anonymous"></script>
  <style>
    /* General Styles */
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      color: #333;
      margin: 0;
      padding: 0;
      text-align: center;
    }

    header {
      background-color: #6200ea;
      color: white;
      padding: 20px;
    }

    h1 {
      margin: 0;
      font-size: 2.5rem;
    }

    .upload-section {
      margin: 20px auto;
      padding: 20px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      max-width: 500px;
    }

    input[type="file"], input[type="number"], button {
      margin: 10px 0;
      padding: 10px;
      width: 100%;
      border: 1px solid #ddd;
      border-radius: 5px;
    }

    button {
      background-color: #6200ea;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background-color: #3700b3;
    }

    .result-section {
      margin: 20px auto;
      padding: 20px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      max-width: 500px;
    }

    footer {
      margin-top: 20px;
      padding: 10px;
      background-color: #333;
      color: white;
    }

    .ad-container {
      margin: 20px auto;
      max-width: 728px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Compressify</h1>
    <p>World's Best Image Compression Tool</p>
  </header>

  <main>
    <!-- AdSense Banner Ad -->
    <div class="ad-container">
      <ins class="adsbygoogle"
           style="display:block"
           data-ad-client="ca-pub-YOUR_AD_CLIENT_ID"
           data-ad-slot="YOUR_AD_SLOT_ID"
           data-ad-format="auto"
           data-full-width-responsive="true"></ins>
      <script>
        (adsbygoogle = window.adsbygoogle || []).push({});
      </script>
    </div>

    <section class="upload-section">
      <h2>Upload Your Image</h2>
      <input type="file" id="imageInput" accept="image/*">
      <label for="compressionLevel">Compression Level (1-10):</label>
      <input type="number" id="compressionLevel" min="1" max="10" value="5">
      <button id="compressBtn">Compress Image</button>
    </section>

    <section class="result-section">
      <h2>Compressed Image</h2>
      <div id="compressedImageContainer"></div>
      <a id="downloadLink" style="display:none;">Download Compressed Image</a>
    </section>

    <!-- AdSense In-Feed Ad -->
    <div class="ad-container">
      <ins class="adsbygoogle"
           style="display:block"
           data-ad-client="ca-pub-YOUR_AD_CLIENT_ID"
           data-ad-slot="YOUR_AD_SLOT_ID"
           data-ad-format="auto"
           data-full-width-responsive="true"></ins>
      <script>
        (adsbygoogle = window.adsbygoogle || []).push({});
      </script>
    </div>
  </main>

  <footer>
    <p>Author: Arnav</p>
    <p>&copy; 2023 Compressify. All rights reserved.</p>
  </footer>

  <script>
    // JavaScript for Image Compression
    document.getElementById('compressBtn').addEventListener('click', function () {
      const fileInput = document.getElementById('imageInput');
      const compressionLevel = document.getElementById('compressionLevel').value;
      const compressedImageContainer = document.getElementById('compressedImageContainer');
      const downloadLink = document.getElementById('downloadLink');

      if (fileInput.files.length === 0) {
        alert('Please upload an image.');
        return;
      }

      const file = fileInput.files[0];
      const reader = new FileReader();

      reader.onload = function (event) {
        const img = new Image();
        img.src = event.target.result;

        img.onload = function () {
          const canvas = document.createElement('canvas');
          const ctx = canvas.getContext('2d');
          canvas.width = img.width;
          canvas.height = img.height;
          ctx.drawImage(img, 0, 0);

          // Adjust quality based on compression level
          const quality = 1 - (compressionLevel / 10);

          canvas.toBlob(function (blob) {
            const compressedUrl = URL.createObjectURL(blob);
            compressedImageContainer.innerHTML = `<img src="${compressedUrl}" alt="Compressed Image">`;
            downloadLink.href = compressedUrl;
            downloadLink.download = `compressed-image-${compressionLevel}.jpg`;
            downloadLink.style.display = 'block';
          }, 'image/jpeg', quality);
        };
      };

      reader.readAsDataURL(file);
    });
  </script>
</body>
</html>

<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>مدرسه شهدای هویزه</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      font-family: 'Vazir', Arial, sans-serif;
      background: linear-gradient(to bottom, #1e3a8a, #6b21a8);
    }
    .star {
      color: gold;
    }
    .empty-star {
      color: #d1d5db;
    }
    .school-logo {
      width: 70px;
      height: 70px;
      background: linear-gradient(135deg, #1e3a8a, #6b21a8);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: bold;
      border: 2px solid gold;
      margin: 0 auto;
      position: relative;
      font-size: 0.65rem;
      text-align: center;
      line-height: 1.2;
      padding: 5px;
    }
    .stars-around {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
    }
    .star-around {
      position: absolute;
      color: gold;
      font-size: 0.5rem;
    }
    .slide-down {
      animation: slideDown 0.5s ease-out;
    }
    @keyframes slideDown {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
  </style>
</head>
<body class="text-gray-800">
  <script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
  </script>

  <header class="bg-blue-600 text-white p-4 text-center">
    <div class="school-logo mb-2">
      مدرسه شهدای هویزه منطقه ۱۶ تهران
      <div class="stars-around">
        <div class="star-around" style="top: 0; left: 50%; transform: translateX(-50%);">★</div>
        <div class="star-around" style="top: 10%; left: 85%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 32%; left: 95%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 50%; left: 100%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 68%; left: 95%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 90%; left: 85%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="bottom: 0; left: 50%; transform: translateX(-50%);">★</div>
        <div class="star-around" style="top: 90%; left: 15%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 68%; left: 5%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 50%; left: 0; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 32%; left: 5%; transform: translate(-50%, -50%);">★</div>
        <div class="star-around" style="top: 10%; left: 15%; transform: translate(-50%, -50%);">★</div>
      </div>
    </div>
    <h1 class="text-2xl font-bold">مدرسه شهدای هویزه</h1>
    <button id="menu-toggle" class="sm:hidden focus:outline-none mt-2">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
      </svg>
    </button>
  </header>

  <nav id="nav-menu" class="bg-blue-500 text-white p-4 hidden sm:block">
    <div class="container mx-auto flex nav-menu">
      <a href="#home" class="px-4 py-2 hover:bg-blue-700">خانه</a>
      <button onclick="toggleAboutSchool()" class="px-4 py-2 hover:bg-blue-700 focus:outline-none">درباره مدرسه</button>
      <button onclick="toggleContact()" class="px-4 py-2 hover:bg-blue-700 focus:outline-none">تماس با ما</button>
      <button onclick="toggleSiteManager()" class="px-4 py-2 hover:bg-blue-700 focus:outline-none">مدیریت سایت</button>
      <button onclick="togglePrincipal()" class="px-4 py-2 hover:bg-blue-700 focus:outline-none">مدیر مدرسه</button>
    </div>
  </nav>

  <div id="site-manager-info" class="hidden transition-all duration-500 bg-white text-right text-sm text-gray-800 p-4 mx-4 my-2 rounded-xl shadow-lg slide-down">
    <p><strong>درباره من:</strong></p>
    <p>این شخص (امیرحسین نوروزی) این سایت را با هدف معرفی مدرسه شهدای هویزه منطقه ۱۶ تهران طراحی کرده است. او دانش‌آموز کلاس ۹۰۴ در این مدرسه می‌باشد.</p>
  </div>

  <div id="about-school-info" class="hidden transition-all duration-500 bg-white text-right text-sm text-gray-800 p-4 mx-4 my-2 rounded-xl shadow-lg slide-down">
    <p><strong>سال تاسیس:</strong> ۱۳۶۰</p>
    <p><strong>نوع مدرسه:</strong> دولتی (عادی)</p>
    <p><strong>تعداد دانش‌آموزان مدرسه:</strong> بیش از ۴۰۰ نفر</p>
  </div>

  <div id="contact-info" class="hidden transition-all duration-500 bg-white text-right text-sm text-gray-800 p-4 mx-4 my-2 rounded-xl shadow-lg slide-down">
    <p>شماره تلفن در پایین سایت درج شده</p>
  </div>

  <div id="principal-info" class="hidden transition-all duration-500 bg-white text-right text-sm text-gray-800 p-4 mx-4 my-2 rounded-xl shadow-lg slide-down">
    <p><strong>مدیر مدرسه:</strong> آقای غنی آبادی</p>
  </div>

  <main class="container mx-auto p-4">
    <section id="home" class="mb-8">
      <h2 class="text-xl font-bold mb-4 text-white">خوش آمدید</h2>
      <p class="text-gray-200">خوش آمدید! ما در این سایت هدف معرفی مدرسه شهدای هویزه را برای شما داریم.</p>
    </section>

    <section id="about" class="mb-8">
      <h2 class="text-xl font-bold mb-4 text-white">درباره مدرسه</h2>
      <p class="text-gray-200">این یک مدرسه عادی در منطقه ۱۶ تهران می‌باشد که در سال ۱۳۶۰ تاسیس شده است. این مدرسه به دلیل حیاط بزرگ و امکاناتی از این قبیل آوازه‌ای بلند در منطقه ۱۶ تهران دارد.</p>
    </section>

    <section id="contact" class="mb-8">
      <h2 class="text-xl font-bold mb-4 text-white">تماس با ما</h2>
      <div class="text-gray-200 space-y-2">
        <p>55343311 - 55324991</p>
        <p>ساعت پاسخگویی: از ۷:۳۰ صبح تا ۱۲:۳۰ بعد از ظهر</p>
      </div>
    </section>

    <section id="principal" class="mb-8">
      <h2 class="text-xl font-bold mb-4 text-white">مدیر مدرسه</h2>
    </section>

    <section id="feedback" class="mb-8">
      <h2 class="text-xl font-bold mb-4 text-white">دیدگاه دانش‌آموزان</h2>
      <div class="bg-white p-4 rounded-lg shadow-md">
        <h3 class="text-lg font-semibold flex items-center">معین جعفری‌نیا
          <span class="ml-2 flex">
            <svg class="w-5 h-5 star" fill="currentColor" viewBox="0 0 20 20"><path d="M10 15l-5.878 3.09 1.122-6.545L.488 6.91l6.561-.955L10 0l2.951 5.955 6.561.955-4.756 4.635 1.122 6.545z"/></svg>
            <svg class="w-5 h-5 star" fill="currentColor" viewBox="0 0 20 20"><path d="M10 15l-5.878 3.09 1.122-6.545L.488 6.91l6.561-.955L10 0l2.951 5.955 6.561.955-4.756 4.635 1.122 6.545z"/></svg>
            <svg class="w-5 h-5 star" fill="currentColor" viewBox="0 0 20 20"><path d="M10 15l-5.878 3.09 1.122-6.545L.488 6.91l6.561-.955L10 0l2.951 5.955 6.561.955-4.756 4.635 1.122 6.545z"/></svg>
            <svg class="w-5 h-5 empty-star" fill="currentColor" viewBox="0 0 20 20"><path d="M10 15l-5.878 3.09 1.122-6.545L.488 6.91l6.561-.955L10 0l2.951 5.955 6.561.955-4.756 4.635 1.122 6.545z"/></svg>
            <svg class="w-5 h-5 empty-star" fill="currentColor" viewBox="0 0 20 20"><path d="M10 15l-5.878 3.09 1.122-6.545L.488 6.91l6.561-.955L10 0l2.951 5.955 6.561.955-4.756 4.635 1.122 6.545z"/></svg>
          </span>
        </h3>
        <p class="text-gray-700 mt-2">مدرسه خوبیه مخصوصاً سرایدارش که همیشه باهاش حال میکنم</p>
        <p class="text-gray-400 text-sm mt-2">تاریخ: ۲۵ آوریل ۲۰۲۵</p>
      </div>
    </section>
  </main>

  <script>
    document.getElementById('menu-toggle').addEventListener('click', function () {
      document.getElementById('nav-menu').classList.toggle('hidden');
    });

    function toggleSiteManager() {
      const section = document.getElementById('site-manager-info');
      section.classList.toggle('hidden');
      if (!section.classList.contains('hidden')) {
        section.classList.add('slide-down');
      }
    }

    function toggleAboutSchool() {
      const section = document.getElementById('about-school-info');
      section.classList.toggle('hidden');
      if (!section.classList.contains('hidden')) {
        section.classList.add('slide-down');
      }
    }

    function toggleContact() {
      const section = document.getElementById('contact-info');
      section.classList.toggle('hidden');
      if (!section.classList.contains('hidden')) {
        section.classList.add('slide-down');
      }
    }

    function togglePrincipal() {
      const section = document.getElementById('principal-info');
      section.classList.toggle('hidden');
      if (!section.classList.contains('hidden')) {
        section.classList.add('slide-down');
      }
    }
  </script>

<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'935e8af8e9f31361',t:'MTc0NTU5MTQ3NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
</body>
</html>

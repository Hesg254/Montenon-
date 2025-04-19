<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    </head>
    <body>Verification: 31f0531e4e2a74bf</body>
</html>
<meta name='viewport' content='width=device-width, initial-scale=1'/><!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Montenon - Фото-Публикатор</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background-color: #4285f4;
            color: white;
            padding: 1rem;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .container {
            max-width: 100%;
            padding: 0 15px;
            margin: 0 auto;
        }
        
        .upload-section {
            background: white;
            padding: 1rem;
            margin: 1rem 0;
            border-radius: 8px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        
        .btn {
            display: inline-block;
            background: #4285f4;
            color: white;
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            text-decoration: none;
            font-size: 1rem;
        }
        
        .btn:hover {
            background: #3367d6;
        }
        
        .gallery {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
            margin: 1rem 0;
        }
        
        .photo-card {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        
        .photo-card img {
            width: 100%;
            height: auto;
            display: block;
        }
        
        .photo-info {
            padding: 0.5rem;
        }
        
        footer {
            text-align: center;
            padding: 1rem;
            background: #4285f4;
            color: white;
            margin-top: 1rem;
        }
        
        @media (min-width: 768px) {
            .gallery {
                grid-template-columns: repeat(3, 1fr);
            }
        }
        
        /* Модальное окно */
        .modal {
            display: none;
            position: fixed;
            z-index: 200;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.9);
        }
        
        .modal-content {
            margin: auto;
            display: block;
            width: 90%;
            max-width: 700px;
            max-height: 90%;
        }
        
        .close {
            position: absolute;
            top: 15px;
            right: 35px;
            color: #f1f1f1;
            font-size: 40px;
            font-weight: bold;
            transition: 0.3s;
        }
        
        .close:hover {
            color: #bbb;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <h1>Montenon - Фото-Публикатор</h1>
    </header>
    
    <div class="container">
        <section class="upload-section">
            <h2>Загрузить фото</h2>
            <form id="upload-form">
                <input type="file" id="photo-upload" accept="image/*" style="margin: 1rem 0;">
                <input type="text" id="photo-title" placeholder="Название фото" style="width: 100%; padding: 0.5rem; margin-bottom: 1rem;">
                <textarea id="photo-description" placeholder="Описание фото" style="width: 100%; padding: 0.5rem; margin-bottom: 1rem; min-height: 100px;"></textarea>
                <button type="submit" class="btn">Опубликовать</button>
            </form>
        </section>
        
        <section class="gallery-section">
            <h2>Галерея</h2>
            <div class="gallery" id="photo-gallery">
                <!-- Пример фото -->
                <div class="photo-card">
                    <img src="https://via.placeholder.com/300" alt="Пример фото" onclick="openModal(this)">
                    <div class="photo-info">
                        <h3>Пример фото</h3>
                        <p>Это пример описания фотографии.</p>
                        <small>01.01.2023</small>
                    </div>
                </div>
                
                <!-- Здесь будут добавляться новые фото через JS -->
            </div>
        </section>
    </div>
    
    <!-- Модальное окно для просмотра фото -->
    <div id="image-modal" class="modal">
        <span class="close" onclick="closeModal()">&times;</span>
        <img class="modal-content" id="modal-image">
    </div>
    
    <footer>
        <p>© 2023 Montenon - Фото-Публикатор. Все права защищены.</p>
    </footer>
    
    <script>
        // Обработка формы загрузки
        document.getElementById('upload-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const fileInput = document.getElementById('photo-upload');
            const titleInput = document.getElementById('photo-title');
            const descInput = document.getElementById('photo-description');
            
            if (fileInput.files.length === 0) {
                alert('Пожалуйста, выберите фото!');
                return;
            }
            
            const file = fileInput.files[0];
            const reader = new FileReader();
            
            reader.onload = function(e) {
                const photoUrl = e.target.result;
                addPhotoToGallery(photoUrl, titleInput.value, descInput.value);
                
                // Очистка формы
                fileInput.value = '';
                titleInput.value = '';
                descInput.value = '';
            };
            
            reader.readAsDataURL(file);
        });
        
        // Добавление фото в галерею
        function addPhotoToGallery(photoUrl, title, description) {
            const gallery = document.getElementById('photo-gallery');
            
            const photoCard = document.createElement('div');
            photoCard.className = 'photo-card';
            
            const img = document.createElement('img');
            img.src = photoUrl;
            img.alt = title;
            img.onclick = function() { openModal(this); };
            
            const photoInfo = document.createElement('div');
            photoInfo.className = 'photo-info';
            
            const h3 = document.createElement('h3');
            h3.textContent = title || 'Без названия';
            
            const p = document.createElement('p');
            p.textContent = description || 'Нет описания';
            
            const small = document.createElement('small');
            const now = new Date();
            small.textContent = now.toLocaleDateString();
            
            photoInfo.appendChild(h3);
            photoInfo.appendChild(p);
            photoInfo.appendChild(small);
            
            photoCard.appendChild(img);
            photoCard.appendChild(photoInfo);
            
            gallery.insertBefore(photoCard, gallery.firstChild);
        }
        
        // Работа с модальным окном
        function openModal(img) {
            const modal = document.getElementById('image-modal');
            const modalImg = document.getElementById('modal-image');
            
            modal.style.display = 'block';
            modalImg.src = img.src;
        }
        
        function closeModal() {
            document.getElementById('image-modal').style.display = 'none';
        }
    </script>
</body>
</html><html></html>

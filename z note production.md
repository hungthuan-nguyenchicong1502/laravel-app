# 1. Bật chế độ bảo trì để người dùng không vào phá lúc đang deploy
php artisan down --refresh=15 --retry=60

# 2. Kéo code mới nhất từ Git về
git pull origin main

# 3. Cài đặt tối ưu các package Composer (Không lấy package dev, copy cứng path repo)
COMPOSER_MIRROR_PATH_REPOS=1 composer install --no-dev --optimize-autoloader

# 4. Chạy cập nhật database
php artisan migrate --force

# 5. Xóa sạch cache cũ và làm mới toàn bộ cache cấu hình
php artisan config:cache
php artisan route:cache
php artisan view:cache

# 6. Tải lại cấu hình OPcache của PHP (Nếu server có cài đặt) để nhận code mới lập tức
# php -r "opcache_reset();"

# 7. Khởi động lại các tiến trình chạy ngầm (Queue workers) để tụi nó nhận code mới
php artisan queue:restart

# 8. Tắt chế độ bảo trì, đưa website hoạt động trở lại
php artisan up
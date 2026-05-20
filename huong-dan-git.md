# Hướng Dẫn Sử Dụng Git

## 1. Cài Đặt Git
Tải về tại: https://git-scm.com/downloads  
Kiểm tra cài đặt thành công:
```bash
git --version
```

---

## 2. Cấu Hình Ban Đầu
```bash
git config --global user.name "Tên của bạn"
git config --global user.email "email@example.com"
```

---

## 3. Khởi Tạo Repository

### Tạo repo mới
```bash
git init
```

### Clone repo từ remote
```bash
git clone https://github.com/username/repository.git
```

---

## 4. Các Lệnh Cơ Bản Hàng Ngày

### Kiểm tra trạng thái
```bash
git status
```

### Xem lịch sử commit
```bash
git log
git log --oneline   # Dạng rút gọn
```

### Thêm file vào staging area
```bash
git add ten-file.txt        # Thêm 1 file
git add .                   # Thêm tất cả file thay đổi
```

### Commit thay đổi
```bash
git commit -m "Mô tả thay đổi của bạn"
```

### Kết hợp add và commit (file đã được track)
```bash
git commit -am "Mô tả thay đổi"
```

---

## 5. Làm Việc Với Remote

### Xem danh sách remote
```bash
git remote -v
```

### Thêm remote
```bash
git remote add origin https://github.com/username/repository.git
```

### Đẩy code lên remote
```bash
git push origin main        # Push lên nhánh main
git push -u origin main     # Push và set upstream (lần đầu)
```

### Kéo code từ remote về
```bash
git pull origin main
```

### Fetch (tải về nhưng chưa merge)
```bash
git fetch origin
```

---

## 6. Làm Việc Với Nhánh (Branch)

### Xem danh sách nhánh
```bash
git branch          # Nhánh local
git branch -a       # Tất cả nhánh kể cả remote
```

### Tạo nhánh mới
```bash
git branch ten-nhanh
```

### Chuyển sang nhánh khác
```bash
git checkout ten-nhanh
git switch ten-nhanh        # Cách mới hơn
```

### Tạo và chuyển sang nhánh mới ngay
```bash
git checkout -b ten-nhanh
git switch -c ten-nhanh     # Cách mới hơn
```

### Merge nhánh vào nhánh hiện tại
```bash
git merge ten-nhanh
```

### Xóa nhánh
```bash
git branch -d ten-nhanh     # Xóa nhánh local (an toàn)
git branch -D ten-nhanh     # Xóa nhánh local (bắt buộc)
git push origin --delete ten-nhanh   # Xóa nhánh remote
```

---

## 7. Hoàn Tác Thay Đổi

### Bỏ thay đổi chưa add (working directory)
```bash
git restore ten-file.txt
git checkout -- ten-file.txt    # Cách cũ
```

### Bỏ file khỏi staging area (đã git add)
```bash
git restore --staged ten-file.txt
git reset HEAD ten-file.txt     # Cách cũ
```

### Hoàn tác commit cuối (giữ lại thay đổi)
```bash
git reset --soft HEAD~1
```

### Hoàn tác commit cuối (xóa luôn thay đổi)
```bash
git reset --hard HEAD~1
```

### Tạo commit đảo ngược (an toàn hơn khi đã push)
```bash
git revert HEAD
```

---

## 8. Stash (Lưu Tạm Thay Đổi)

### Lưu tạm thay đổi hiện tại
```bash
git stash
git stash push -m "Mô tả"   # Có ghi chú
```

### Xem danh sách stash
```bash
git stash list
```

### Lấy lại thay đổi đã stash
```bash
git stash pop               # Lấy stash mới nhất và xóa khỏi danh sách
git stash apply stash@{0}   # Lấy stash cụ thể, không xóa
```

### Xóa stash
```bash
git stash drop stash@{0}    # Xóa 1 stash
git stash clear             # Xóa tất cả stash
```

---

## 9. Tag

### Tạo tag
```bash
git tag v1.0.0
git tag -a v1.0.0 -m "Phiên bản 1.0.0"   # Tag có chú thích
```

### Xem danh sách tag
```bash
git tag
```

### Push tag lên remote
```bash
git push origin v1.0.0
git push origin --tags      # Push tất cả tag
```


---

## 10. Quy Trình Làm Việc Thông Thường

```
1. git pull origin main          # Cập nhật code mới nhất
2. git checkout -b feature/ten   # Tạo nhánh mới cho tính năng
3. (... viết code ...)
4. git add .                     # Thêm thay đổi
5. git commit -m "Mô tả"        # Commit
6. git push origin feature/ten   # Push lên remote
7. Tạo Pull Request trên GitHub
8. Sau khi merge: git checkout main && git pull
```

---

## 11. Một Số Lệnh Hữu Ích Khác

```bash
git diff                    # Xem thay đổi chưa staged
git diff --staged           # Xem thay đổi đã staged
git show HEAD               # Xem chi tiết commit cuối
git blame ten-file.txt      # Xem ai thay đổi từng dòng
git clean -fd               # Xóa file/folder chưa được track
git log --graph --oneline   # Xem lịch sử dạng đồ thị
```

---

## 12. File .gitignore
Tạo file `.gitignore` để bỏ qua các file không cần track:
```
# Ví dụ .gitignore
node_modules/
*.log
.env
.DS_Store
dist/
build/
```



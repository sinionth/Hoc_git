## Cài đặt git trên ubuntu
`apt-get install git -y`
## Cấu hình thiết lập tên, Email
```
git config --global user.name "dung1101"
git config --global user.email "mrbeo1221119@gmail.com"
```
## Kiểm tra cấu hình
```
cat ~/.gitconfig
git --list
```
## Thiết lập repository
Repository (kho chứa) là nơi lưu trữ mã nguồn và người khác có thể sao chép (clone) lại mã nguồn để làm việc.Có 2 loại repo:
- Local Repository (Kho chứa trên máy cá nhân)
- Remote Repository (Kho chứa trên một máy chủ từ xa).
###  Tạo Local Repository
```
cd [thư mục muốn lưu trữ repo]
git init [tên repo]
```
###  Tạo Remote Repository
Sử dụng Github làm repo remote, truy cập chia sẻ từ xa
`git clone [repo link]` để clone về và làm việc
## Thao tác cơ bản 
### Thực hiện chỉnh sửa remote repo của chính mình
![](so_do.png)
<br>working directory: thư mục chứa repo mà ta đã clone về để làm việc
<br>staging area: là khu vực lưu trữ những thay đổi trên tập tin so sánh giữa repo chính và repo clone trước commit
<br>clone repo: repo mà ta đã clone về từ remote repo
<br>remote repo: repo mà ta cần làm việc 
```
git add .
git commit -m "uptade repo"
git push origin master
```
<br>Trước khi tiến hành ta phải sử dụng `git pull` để update những chỉnh sửa mới nhất của repo để tránh conflict
<br>Khi ta commit nhầm, git cho phép ta undo lại bằng cách
```
git reset HEAD~ --hard
  HEAD~ hoặc HEAD^ hoặc @^ : undo lại 1 commit để undo nhiều commit thì thêm số vào sau HEAD~5
  --hard: loại bỏ tất cả mọi thay đổi kể cả ở trong working directory 
  ngoài ra có lựa chọn khác là --soft thì sẽ dữ lại những thay đổi ở trong working directory
```
<br>Sau khi commit thành công nhưng ta lại muốn thay đổi mà không cần phải tạo commit mới thì ta có thể ghi đè commit mới nhât bằng option `--amend` trong commit
<br>Ta cũng có thể bỏ qua việc add vào staging area để commit thẳng bằng option `-a`
### Thực hiện chỉnh sửa remote repo của người khác
<br>Trước tiên ta phải `fork` repo sau đó mới `clone` về để làm việc
<br>Các bước tiếp theo ta làm như trên 
<br>Do đây là repo của người khác nên sau khi push ta ta tạo một pull request mới để xin phép chủ sở hữu cho phép cập nhật chỉnh sửa
### Chỉnh sửa remote repo
Kiếm tra remote<br>
`git remote -v`<br>
Đổi tên remote<br>
`git remote rename [tên_cũ] [tên_mới]`<br>
Thêm 1 remote<br>
`git remote add [tên_remote] URL`<br>
## Sự khác nhau giữa clone, fetch và pull
3 lệnh để lấy dữ liệu về từ repository nhưng có sự khác nhau:
__git clone__:Sao chép toàn bộ dữ liệu trên repository và sao chép luôn các thiết lập về repository, tức là nó sẽ tự động tạo một master branch trên máy tính.Lệnh này chỉ nên sử dụng khi cần tạo mới Git repo trên máy tính với toàn bộ dữ liệu và thiết lập của một remote repository.<br>
__git pull__:Tự động lấy toàn bộ dữ liệu từ remote repository và gộp vào cái branch hiện tại đang làm việc.
__git fetch__:Lấy toàn bộ dữ liệu từ remote repository nhưng sẽ cho phép gộp thủ công vào một branch nào đó trên thư mục Git ở máy tính.
## 
## xem lịch sử commit
Sử dụng câu lệnh
`git log` để xem hoặc `gt log -p` để xem thông tin chi tiết hơn

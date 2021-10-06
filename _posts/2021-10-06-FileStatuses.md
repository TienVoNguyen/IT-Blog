---
title: Các trạng thái file trong git và github
published: true
---

**Bài viết được tham khảo trên [git-scm.com](git-scm.com), [freetuts](https://freetuts.net/git-ba-trang-thai-committed-staged-modified-1079.html),[The Brown Box](https://hoangvancong.com/2020/05/01/git-03-cac-trang-thai-va-cau-lenh-co-ban-trong-git/)**
# 1. Git là gì?

 *Đầu tiên để biết được các trạng thái của file trong Git các bạn phỉa biết Git là gì* 

 Git là một phần mềm, hệ thống quản lý mã nguồn phân tán. Ban đầu Git được phát triển phục vụ cho Linux nhưng bây giờ bạn có thẻ sử dụng được nó trên cả Windows. Với Git bạn có thể lưu lại lịch sử và trạng thái của các file trong dự án, sau đó bạn có thể rollback về một lịch sử bất kì mà không cần phải backup lại.

 Git sử dụng mô hình phân tán và điều này hoàn toàn ngược với SVN hoặc CSV, mỗi nơi lưu trữ source ta gọi là 1 repo (repository), các lập trình viên sẽ tạo một repo tại máy của mình. Câu hỏi đặt ra là nếu user nào cũng có repo riêng thì việc đụng độ code khi upload mã nguồn lên repo chính thì sao? Điều này hoàn toàn được giải quyết bởi Git sẽ cảnh báo và giúp các lập trình viên biết có sự đụng độ code (conflick) và sẽ yêu cầu họ chỉnh sửa và thay đổi trạng thái hết đụng độ.

 Thông thường ta cần kết hợp với một dịch vụ lưu trữ mã nguồn trực tuyến như Github (repo chính), tại đây các thành viên sẽ dùng lệnh để đẩy dữ liệu từ máy tính của cá nhân họ lên Github, điều này hoàn toàn an toàn và bảo mật bởi mỗi repo của các lập trình viên đều là bản sao thật của repo trên github, vì vậy khi server bị down thì các thành viên vẫn có mã nguồn backup trên máy tính của họ.

# 2. Các trạng thái của file.

![4](https://user-images.githubusercontent.com/91824682/136139024-5d1362fd-21e6-4062-8e59-ef2175f15dd4.PNG)

 Các trạng thái file của Git là một phần rất quan trọng mà bạn cần phải hiểu trước khi hiểu sâu hơn và commit.

 Tất cả các file có liên kết đến một remote repository (như github) đều được lưu chữ ở trong 2 nơi:
* **Local Repository**: Tất cả các thay đổi đã được đánh dấu (commit) sẽ được lưu ở local repo cho đến khi chúng được đẩy (push) lên remote repo. Các thay đổi này chỉ tồn tại ở trên local của người dùng ko visible với những người khác.

* **Remote Repository**: Các thay đổi đã được commit tại local repo sẽ được cập nhật lên remote repo. Lúc này những người làm việc chung cùng repo đó có thể cập nhật/kéo (pull) các thay đổi đó về máy của mình.

Trong bài này các câu lệnh chúng ta thực hiện sẽ chủ yếu nằm ở Local Repo, và cuối cùng chúng ta sẽ đẩy (push) các thay đổi đó lên Remote Repo (github).

Tất cả các file ở Local Repo đều ở một trong 2 trạng thái:

* **Untracked Files**: Các file này dù có thay đổi / thêm / xoá thì git cũng không quan tâm, vì nó ko nằm trong danh sách theo dõi của nó.

Khi chúng ta sử dụng lệnh “git status” thì các file này sẽ có title là “***Untracked files***”

![1](https://user-images.githubusercontent.com/91824682/136137168-458f71bd-b06e-4de8-8c05-efb01e25de71.PNG)

* **Tracked Files**: Những files đã được thêm vào danh sách theo dõi của git được gọi là Tracked Files, những file này khi chúng ta thay đổi / thêm / xoá thì git sẽ nhận biết được điều đó và lưu các thay đổi này lại theo yêu cầu của chúng ta.

Trong các Tracked Files được git theo dõi lại có 3 trạng thái sau: committed, modified, và staged.

* **Modified** có nghĩa là bạn đã thay đổi tập tin nhưng chưa commit vào cơ sở dữ liệu, tức là bạn chưa sử dụng lệnh **git add** và **git commit**.

>Các files bị thay đổi sẽ có title **“<span style="color: red;">Changes not staged for commit</span>”** khi chúng ta **“git status"**.

![2](https://user-images.githubusercontent.com/91824682/136137884-b523817c-70c9-4c6e-a508-91641fcfbcd9.PNG)

* **Staged** là bạn đã đánh dấu sẽ commit phiên bản hiện tại của một tập tin đã chỉnh sửa trong lần commit sắp tới. Trạng thái này xảy ra khi bạn sử dụng lệnh git add \<file_name> nhưng chưa commit.

> Các files bị thay đổi sẽ có title “<span style="color: rgb(5, 255, 80);">Changes to be committed</span>” khi chúng ta **“git status”**.

![3](https://user-images.githubusercontent.com/91824682/136138383-b7bfdee3-3046-473c-9c9a-e6b9d3b7f767.PNG)

* **Committed(Unmodified)** có nghĩa là dữ liệu đã được lưu trữ một cách an toàn trong cơ sở dữ liệu, tức là những gì bạn đã commit thành công.

> Lúc này khi chúng ta **“git status”** sẽ không còn thấy các file này nữa.

Như vậy với 3 trạng thái này đã tạo ra ba phần riêng biệt của một dự án có sử dụng Git.

# 3. Ba khu vực riêng biệt của 1 dự án sử dụng GIT.

![5](https://user-images.githubusercontent.com/91824682/136139423-43d7a6b0-80b5-4338-a085-a3df34195e70.PNG)

1. **Khu vực Git** (Git directory):

    Là thư mục lưu trữ siêu dữ liệu (metadata) và cơ sở dữ liệu của dự án, thư mục này sẽ bị ẩn bởi hệ điều hành Windows nên bạn phải bật chức năng hiển thị file ẩn thì mới thấy được.  Khu vực này sẽ tiếp nhận và lưu trữ các commit từ stage area.
2. **Khu vực làm việc** (Working directory):  

    Nếu bạn không sử dụng Remote repository thì đây là bản sao của dự án, còn không thì đây là thư muc chính của dự án và branch master chính là bản chính, còn các branch mới tạo là branch bản sao.

3. **Khu vực tổ chức** (staging area): 

    Đây là một tập tin đơn giản nằm trong thư mục git, nó sẽ chứa thông tin về trạng thái của một file trong dự án.

>Như vậy nếu bạn thay đổi một file nhưng chưa sử dụng lệnh git add và git commit thì file đó ở trạng thái **Modified**, còn nếu bạn đã sử dụng lệnh git add thì sẽ ở trạng thái **Staged**, còn đã commit thì sẽ ở trạng thái **Committed**.

```
Nếu bài viết này giúp bạn hiểu hơn về Git thì hãy chia sẻ nhé!

Thank you.
```

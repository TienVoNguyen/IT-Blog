---
title: Hướng dẫn tạo và chạy file jar trên Command Prompt
published: true
---

[Link youtube hướng dẫn](https://www.youtube.com/channel/UCpOw9sCBe9KDygkYJPUlcbQ)

# [](#header-1)Tệp JAR là gì và cách tạo mở một tệp JAR

  Bạn đã bao giờ gặp file JAR (.jar) chưa? 

  Bạn có muốn chạy 1 chương trình java của mình mà không cần dùng IDE: NetBeans, Eclipse...? 
  
  Bài viết dưới đây sẽ giải thích file JAR là gì, cách tạo file jar từ 1 project và cách mở file JAR trong Windows 10 bằng Command Prompt.

## [](#header-1)1. File JAR là gì?

  JAR là viết tắt của Java ARchive. Như tên gọi của nó cho thấy, đó là một file lưu trữ. Điều này có nghĩa rằng đó là một file duy nhất chứa các file khác được đóng gói cùng nhau vì những lý do như tính di động và dung lượng lưu trữ giảm.

  Tệp .jar là tệp gói Java. Nó tương tự như một tệp ZIP trong Windows nơi tập hợp các tệp và tài nguyên được thu thập thành một tệp duy nhất để dễ dàng vận chuyển hoặc cài đặt. Các gói phần mềm thường là khép kín và sẽ bao gồm tất cả mọi thứ cần thiết để làm cho gói thực hiện mục đích sử dụng của nó.

  Yếu tố duy nhất của file JAR là chúng chứa một manifest. Đây là một siêu file đặc biệt, nói một cách đơn giản, cho JAR biết cách hoạt động và lưu giữ thông tin về các file bên trong.

  File JAR cũng có thể chứa file CLASS (code Java đã biên dịch), file âm thanh, file hình ảnh, v.v... Sau đó, file JAR có thể được đọc và chạy như một yêu cầu duy nhất bởi Runtime Environment.

  JAR có thể được sử dụng cho mọi mục đích trên desktop và điện thoại di động. Ví dụ, đó có thể là game, chủ đề ứng dụng hoặc add-on trình duyệt.

  Để chạy các tệp Java trên máy tính của bạn, bạn cần cài đặt Java Runtime Environment (JRE) để có thể mở và chạy các tệp .jar. Thời gian chạy Java là các gói nhỏ được viết bằng Java thường hoạt động với trình duyệt hoặc ứng dụng để thực hiện một tác vụ như phát video.

## [](#header-2)2. Làm thế nào để tạo file jar từ chính project java của bạn?
[![Video hướng dẫn](https://user-images.githubusercontent.com/91824682/136071799-db3c4a6c-9f66-445f-a077-e43821969e6b.PNG)](https://www.youtube.com/watch?v=RdDHfaX9Co8)


### [](#header-4)B1.  Tìm đến đường dẫn file.

  Đầu tiên để tạo được 1 file jar từ project java bạn cần phải tìm đến đường dẫn của project đó. Sau đó, tìm tới thư mục chứa các file java của project đó. 

```
  VD:"C:\Users\DinhVan\Documents\NetBeansProjects\Lab2\src\bai12"
```

  ![duongdanjava](https://user-images.githubusercontent.com/91824682/135866692-787ef027-55c8-42e6-9942-fdcb01431ed5.PNG)

### [](#header-4)B2.  Tạo thư mục META-INF và file MANIFEST.MF

  Tại thư mục chứa package có các file java tạo một thư mục
  mới tên META-INF. Trong thư mục META-INF tạo một file txt tên MANIFEST.

```
  VD : Thư mục META-INF cùng cấp với bai12 mà tôi định tạo file jar.
```

  ![thumucchuaMETA-INF](https://user-images.githubusercontent.com/91824682/135870259-30839a01-a289-4e0d-b2a9-2661baf1987c.PNG)
     
  Trong file MANIFEST vừa tạo viết: “Main-Class: [Tên package chứa class main].(Tên class main chạy chương trình)”, nếu main class không  trong package nào thì chỉ cần viết  “Main-Class: (Tên class main chạy chương trình)” + Enter xuống 1 dòng. 

```
  VD : "Main-Class: bai12.StaffFrom"
```

  ![manifestmf](https://user-images.githubusercontent.com/91824682/135866688-af1f7331-5e68-47fe-b90e-54e7885cb8b1.png)
 
  Main StaffFrom của người viết trong pack age nên phải đặt đường dẫn bai12.StaffFrom.

  ![bai12StaffFrom](https://user-images.githubusercontent.com/91824682/135871088-b3a896a6-cf66-47df-a15f-e37fba541a15.PNG)
   
  **Lưu ý:  Bạn phải viết đúng theo quy ước nếu không file jar của bạn sẽ không hoạt động.**
   
  Sau khi viết xong bạn lưu lại và đổi định dạng filetxt => .MF   
    
  ![mani](https://user-images.githubusercontent.com/91824682/135871649-43bcc7c9-d423-45b8-ac3c-a07961441190.PNG)

### [](#header-4)B3: Mở Command Prompt và tạo file jar

  Mở command line bằng tổ hợp phím WINDOW + R. "cmd" => ok

  ![cmd](https://user-images.githubusercontent.com/91824682/135872105-b511c9ed-ca60-4a1d-8294-affc9bd6dedf.PNG)

  Dùng lệnh cd để trỏ tới thư mục chứa package có các file java cần chạy.

  ![1](https://user-images.githubusercontent.com/91824682/135866066-771949d6-4c85-43c7-897e-6ff8fcf3c26e.png)

  Gõ lệnh “javac –encoding UTF8 (tên package).*java”. Dòng lệnh này sẽ biên dịch tất cả các file java có trong package của bạn. “-encoding UTF8” sẽ bảo đảm rằng khi dịch chương trình sẽ không lỗi front chữ. Lưu ý: nếu bạn có nhiều package trong chương trình chỉ cần thêm vào lần lượt sau dấu cách.
 
```
  VD: "jar cvfm bai1.jar META-INF\MANIFEST.MF bai12\*.java img"
```

  ![2](https://user-images.githubusercontent.com/91824682/135866075-f2098031-06d3-4af4-ae59-b2d655c0d35d.png)
    
  Gõ lệnh “jar cvfm (tên file jar bạn muốn).jar META-INF\MANIFEST.MF (tên package)\*.class”. dòng lệnh này sẽ gom tất cả các file .class vừa được dịch ở trên vào file .jar của bạn và chỉ đinh main class khi bạn chạy chương trình từ file .MF. Lưu ý: nếu bạn có nhiều package, thư mục chứa hình ảnh, video sử dụng trong chương trình chỉ cần thêm lần lượt vào sau dấu cách.

```
  VD: "jar cvfm bai1.jar META-INF\MANIFEST.MF bai12\*.class img"
```

  ![3](https://user-images.githubusercontent.com/91824682/135866112-6f61fcaa-aa6b-4037-a7c4-0fa3d6c44c5b.PNG)
     
### [](#header-4)B4: Chạy file jar và xem thành quả

  Gõ lệnh: “java –jar <tên file jar>.jar” + ENTER
 
```
  VD: "java -jar bai1.jar"
```

  ![4](https://user-images.githubusercontent.com/91824682/135866115-5c9e2bad-648c-4b22-a9e1-9d7bdcc7329b.PNG)
      
  **Lưu ý: Nếu bạn đã biên dịch chương trình mà không báo lỗi nhưng khi đến B4 chạy lại báo lỗi ”Could not find or load main class …” có nghĩa là bạn đã chỉ đinh sai tên main class hoặc bạn đã viết chưa đúng cú pháp hãy đọc kĩ lại và thực hiện lại việc tạo file .MF và chỉ đinh lại tên main class của bạn.**
    
  ![loi](https://user-images.githubusercontent.com/91824682/135866124-17d6350f-3580-4ca8-ac5e-dea6579d376d.PNG)

  Nguồn tham khảo: 
  [tutorialspoin](https://www.tutorialspoint.com/How-to-run-a-java-program)
  [KhietNguyenVan](https://youtu.be/p19toyYBVpQ)
  [stackoverflow](https://stackoverflow.com/questions/16137713/how-do-i-run-a-java-program-from-the-command-line-on-windows)
```
Nếu thấy hay hãy chia sẻ để mọi người cùng biết
Nếu bạn có cách nào hay hơn hãy cho chúng tôi biết.
Cảm ơn vì đã ghé thăm. Chúc các bạn thành công.
```
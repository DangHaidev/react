# react
everything relative with react

## JSX ?
- Javascript XML được sử dụng trong React, vẫn có thể sử dụng trong VueJS
- Mục đích của JSX được tạo ra để có thể tạo ra các element một cách tường minh và đơn giản. JSX cho phép developer có thể tạo ra các đoạn HTML nhanh chóng, kèm với khả năng có thể chèn các giá trị JS vào bên trong để tạo ra trang web có nội dung động.
#### Jsx không phải là html
  + single parent root
  + className thay vì class
  + style nhận vào là 1 object
  + bọc bên trong dấu `()`
  + component sử dụng tên viết hoa
#### Quy tắc
- Trả về một 1 tử duy nhất
- close all element
## Component là gì?
- Components là những thành phần giao diện (UI) được định nghĩa độc lập, có thể tái sử sụng và hoàn toàn tách biệt nhau.
#### Tạo cpt
    export default function Profile() {
    return <img src="https://i.imgur.com/MK3eW3Am.jpg" alt="Katherine Johnson" />;
    }
#### Sử dụng
    function Profile() {
      return <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />;
    }
    
    export default function Gallery() {
      return (
        <section>
          <h1>Các nhà khoa học tuyệt vời</h1>
          <Profile />
          <Profile />
          <Profile />
        </section>
      );
    }
- `<section>` viết thường, vì vậy React biết rằng chúng ta đang đề cập đến một thẻ HTML.
- `<Profile />` bắt đầu bằng chữ cái viết hoa, vì vậy React biết rằng chúng ta muốn sử dụng component của mình có tên là `Profile`.
#### Lưu ý
- Không tạo component ở trong component khác

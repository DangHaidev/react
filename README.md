# react

everything relative with react

## JSX ?

- Javascript XML được sử dụng trong React, vẫn có thể sử dụng trong VueJS
- Mục đích của JSX được tạo ra để có thể tạo ra các element một cách tường minh và đơn giản. JSX cho phép developer có thể tạo ra các đoạn HTML nhanh chóng, kèm với khả năng có thể chèn các giá trị JS vào bên trong để tạo ra trang web có nội dung động.

#### Jsx không phải là html

- single parent root
- className thay vì class
- style nhận vào là 1 object
- bọc bên trong dấu `()`
- component sử dụng tên viết hoa

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

## Props là gì?

- Props là tham số đầu vào của các cpt trong react ~ ( liên tưởng nó là các thuộc tính trong HTMl)
- Props là một object chứa các thuộc tính

#### Tạo props

    function Profile({ name, image }) {
      return (
        <section>
          <h1>{name}</h1>
          <img src={image} alt={name} />
        </section>
      );
    }

#### Sử dụng props

    export default function Gallery() {
      return (
        <section>
          <h1>Các nhà khoa học tuyệt vời</h1>
          <Profile name="Katherine Johnson" image="https://i.imgur.com/MK3eW3Am.jpg" />
          <Profile name="Ada Lovelace" image="https://i.imgur.com/MK3eW3As.jpg" />
          <Profile name="Grace Hopper" image="https://i.imgur.com/MK3eW3At.jpg" />
        </section>
      );
    }

#### Truyền toàn bộ props

    function Gallery(props) {
      return (
        <div className="card">
          <Profile {...props} />
        </div>
      );
    }

## State trong react

- Là một biến đặc biệt trong react (được gọi là các hooks), khi thay đổi thì react sẽ tính toán lại và re-render lại các component
- Khai báo để sử dụng :
- `const [stateVariable, setStateVariable] = useState(initialValue);` đây là khai báo theo kiểu destructing

#### Cập nhật state của object

- Tạo ra một bản sao. sau đó dùng bản sao cập nhật obj gốc.

  import { useState } from "react";

<<<<<<< HEAD
export default function UserProfile() {
// Khởi tạo một đối tượng user trong state
const [user, setUser] = useState({
name: "John Doe",
age: 30,
email: "johndoe@example.com",
});
const updateUserEmail = (newEmail) => {
// Không nên thay đổi trạng thái đối tượng user trực tiếp
// Tạo một bản sao mới và cập nhật state
const updatedUser = { ...user, email: newEmail };
setUser(updatedUser);
};

return (

  <div>
  <p>Tên: {user.name}</p>
  <p>Tuổi: {user.age}</p>
  <p>Email: {user.email}</p>
  <button onClick={() => updateUserEmail("newemail@example.com")}>
  Đổi Email
  </button>
  </div>
  );
  }

=======
export default function UserProfile() {
// Khởi tạo một đối tượng user trong state
const [user, setUser] = useState({
name: "John Doe",
age: 30,
email: "<johndoe@example.com>",
});
const updateUserEmail = (newEmail) => {
// Không nên thay đổi trạng thái đối tượng user trực tiếp
// Tạo một bản sao mới và cập nhật state
const updatedUser = { ...user, email: newEmail };
setUser(updatedUser);
};

    return (
      <div>
        <p>Tên: {user.name}</p>
        <p>Tuổi: {user.age}</p>
        <p>Email: {user.email}</p>
        <button onClick={() => updateUserEmail("newemail@example.com")}>
        Đổi Email
        </button>
      </div>
    );
    }

> > > > > > > dc202b6b89b8213aebb80808041c89763af0fd88

## UseEffect trong React

- là một hook của react dùng để side effects sau khi component được render.
- Một số ví dụ về side effects:
  | Tác vụ | Ví dụ |
  | ------------------------- | -------------------------------------------- |
  | Gọi API | Lấy dữ liệu từ server |
  | Thay đổi DOM | Tự động scroll, đặt focus |
  | Set timeout / interval | Đếm giờ, thực hiện hành động định kỳ |
  | Lưu vào localStorage | Lưu trạng thái form, giỏ hàng |
  | Đồng bộ với sự kiện ngoài | Lắng nghe sự kiện từ bàn phím, window resize |

## Life cycle trong react (class component)

#### Mounting

- Có 3 phương thức:
  - `ComponentWillMount()`
  - `Render()`
  - `ComponentDidMount()` : nơi thực hiện hàm AJAX, axios request, DOM hay update state.

#### Updation

- `componentWillReceiveProps()` chạy khi cpt con nhận props từ cpt cha
- `shouldComponentUpdate()`: Hàm này có thể nói là nó tăng hiệu năng của React lên. Nếu như return false thì các phương thực componentWillUpdate, render, componentDidUpdate sẽ không được chạy nữa(vì mặc định nó return về true để chạy được 3 hàm tiếp theo, nhiều trường hợp mình không cần chạy 3 hàm tiếp theo).
- `componentWillUpdate()` giống với `cptwillMount() chạy trước khi re-render
- `render()` là phương thức chính của React, nó sẽ được gọi mỗi khi một component được render.
- `componentDidUpdate()` sẽ được gọi sau khi component được render.

#### Unmounting

- `componentWillUnmount()` : khi cpt bị remove khỏi dom

## Life cycle trong react (funtion component)

- userEffect chỉ làm 2 việc

  | Class method           | useEffect tương ứng                             |
  | ---------------------- | ----------------------------------------------- |
  | `componentDidMount`    | `useEffect(() => {...}, [])`                    |
  | `componentDidUpdate`   | `useEffect(() => {...}, [deps])`                |
  | `componentWillUnmount` | Cleanup trong `useEffect`: `return () => {...}` |

Dùng trong các giai đoạn:
| Mục đích | Giai đoạn phù hợp |
| ------------------------------ | -------------------------------------------------- |
| Gọi API, fetch dữ liệu | `componentDidMount` / `useEffect(..., [])` |
| Đồng bộ state với props | `getDerivedStateFromProps` |
| Kiểm soát render lại hay không | `shouldComponentUpdate` |
| Lưu scroll, DOM snapshot | `getSnapshotBeforeUpdate` |
| Dọn dẹp timer, event listener | `componentWillUnmount` / cleanup trong `useEffect` |

- setup
- cleanup
  | Class method | useEffect tương ứng |
  | ---------------------- | ----------------------------------------------- |
  | `componentDidMount` | `useEffect(() => {...}, [])` |
  | `componentDidUpdate` | `useEffect(() => {...}, [deps])` |
  | `componentWillUnmount` | Cleanup trong `useEffect`: `return () => {...}` |

Dùng trong các giai đoạn:

| Mục đích                       | Giai đoạn phù hợp                                  |
| ------------------------------ | -------------------------------------------------- |
| Gọi API, fetch dữ liệu         | `componentDidMount` / `useEffect(..., [])`         |
| Đồng bộ state với props        | `getDerivedStateFromProps`                         |
| Kiểm soát render lại hay không | `shouldComponentUpdate`                            |
| Lưu scroll, DOM snapshot       | `getSnapshotBeforeUpdate`                          |
| Dọn dẹp timer, event listener  | `componentWillUnmount` / cleanup trong `useEffect` |

#### React Router

#### Các thành phần trong react router

- `BrowserRouter` là một thành phần được sử dụng để bọc toàn bộ ứng dụng reactjs, sử dụng HTML5 history API (thay đổi url của trang web mà không cần reload lại trang) để giữ cho URL được đồng bộ với trạng thái ứng dụng.
- Route là thành phần để xác định một đường dẫn và liên kết nó với một component React cụ thể. Nếu đường dẫn trên thanh địa chỉ phù hợp với định nghĩa trong Route, component được chỉ định sẽ được hiển thị.

  import { Route } from 'react-router-dom';
  function App() {
  return (
    <div>
          <Route path="/" exact component={Home} />
          <Route path="/about" component={About} />
        </div>
      );
    }

- Link là thành phần tạo ra liên kết giữa các trang mà không làm tải lại trang.

    <nav>
      <ul>
        <li>
          <Link to="/">Trang Chủ</Link>
        </li>
        <li>
          <Link to="/about">Về Chúng Tôi</Link>
        </li>
      </ul>
    </nav>

- Switch được sử dụng để bao bọc các thành phần Route, với Route trang web sẽ render và hiển thị các thành phần đầu tiên phù hợp với địa chỉ. Điều này giúp tránh hiển thị nhiều component cùng lúc.
- Redirect là một thành phần được sử dụng để chuyển hướng người dùng từ một đường dẫn khác. Nếu người dùng truy cập đường dẫn được xác định trong Redirect, họ sẽ được chuyển hướng đến địa chỉ mới.

## NextJS

### NextImage

- Trong Next.js, next/image là một component được tối ưu hóa để hiển thị hình ảnh trên các ứng dụng web. Nó tự động xử lý nhiều tác vụ tối ưu hóa hình ảnh, giúp cải thiện hiệu suất tải trang và trải nghiệm người dùng

#### Các Tính Năng Nổi Bật

- next/image không chỉ đơn giản là một thẻ `<img>` thay thế; nó cung cấp nhiều tính năng quan trọng:
- Tối ưu hóa kích thước: Tự động thay đổi kích thước hình ảnh dựa trên thiết bị của người dùng, giúp giảm dung lượng tải xuống.
- Lazy Loading (Tải Trì Hoãn): Chỉ tải hình ảnh khi nó sắp hiển thị trong khung nhìn của người dùng, giúp trang tải nhanh hơn.
- Định dạng hình ảnh hiện đại: Chuyển đổi hình ảnh sang các định dạng tối ưu như WebP khi trình duyệt hỗ trợ.
- Chống dồn layout (Layout Shift): Tự động thêm placeholder để ngăn trang bị dồn khi hình ảnh tải xong, mang lại trải nghiệm mượt mà hơn.
- Tên file băm: Đổi tên file hình ảnh thành một chuỗi duy nhất để tận dụng bộ nhớ đệm (caching) hiệu quả hơn.

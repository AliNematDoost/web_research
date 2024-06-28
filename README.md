
<h1 dir="rtl" align = "center"> Axios in React Js </h1>

<h1 dir="rtl" > مقدمه  </h1>

<p dir="rtl">
    در برنامه هایی که با استفاده از React Js میسازیم، گاهی لازم است تا برای تبادل اطلاعات با Back-End پروژه داده هایی را ارسال یا دریافت کنیم و سپس داده ها را پردازش کنیم. برای این منظور ابزار ها و روش های گوناگونی وجود دارد. در حالی که بسیاری با ابزارهایی مانند Fetch API آشنایی دارند، کتابخانه قدرتمندی به نام Axios وجود دارد که این فرآیند را بسیار ساده می‌کند. 
</p>


<h1 dir="rtl" >  Axios </h1>

<p dir="rtl">
 Axios مسئول ارسال درخواست ها (asynchronous HTTP requests) به REST endpoints یا بعبارتی همان Back-End پروژه و ارائه نتایج حاصل می‌باشد. در ادامه با ویژگی ها و کارکرد های Axios بیشتر آشنا میشویم. 
  
</p>

<h1 dir="rtl"> استفاده از Axios </h1>

<div dir="rtl">
    همانطور که پیشتر گفته شد از کتابخانه Axios برای ارسال درخواست های HTTP به سمت سرور استفاده می‌شود. در ادامه مثال هایی از به کارگیری Axios برای ارسال درخواست های POST , GET , DELETE را مشاهده خواهیم کرد. به دلیل کاربرد گسترده تر و محبوبیت بیشتر Functional Component ها در میان توسعه دهندگان مثال هایی از به کارگیری Axios در این دسته از component ها را آورده ایم.
</div>

<h1> نصب Axios </h1>

<p>
    برای استفاده از Axios ابتدا باید پکیج های آن را نصب کرد. برای این منظور می‌توان از دستور های زیر استفاده کرد :
</p>    


```cmd
npm install axios
```



<p>
    بعد از نصب Axios برای استفاده باید آن را در React component اضافه کنید. برای import کردن Axios از این دستور باید استفاده کرد :
</p>


```jsx
import axios from "axios";
```




<h2> ارسال درخواست GET با استفاده از Axios </h2>

<p>
    در این مثال با استفاده از سرویس JSONPlaceholder API قصد داریم با استفاده از Axios داده هایی را دریافت کرده و به کاربر نمایش دهیم.
</p>

```jsx
import React, { useState, useEffect } from "react";
import axios from "axios";

const GetData = () => {
  const [data, setData] = useState([]);

  const fetchData = async () => {
    try {
      const response = await axios.get("https://jsonplaceholder.typicode.com/posts");
      setData(response.data);
    } catch (error) {
      console.error("Error fetching data:", error);
    }
  };

  useEffect(() => {
    fetchData();
  }, []);

  return (
    <div>
      <h2>Posts:</h2>
      <ul>
        {data.map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  );
};

export default GetData;
```
<h5> بررسی مثال بالا </h5>

<p>
    در این مثال، تابع fetchData را ساخته ایم که با استفاده از Axios درخواست GET را به سمت سرویس JSONPlaceholder API ارسال میکند. در ادامه پاسخ دریافت شده از سرور را در یک state به نام Data ( با مقدار اولیه یک آرایه تهی ) که پیشتر ساخته شده  ذخیره می‌کنیم. با استفاده از useState متدی به نام setData برای تغییر و مقداردهی Data تعیین شده است.
    در ادامه با استفاده از Hook تابع fetchData را پس از اجرای برنامه فرا خوانی میکنیم
    
</p>

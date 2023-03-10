![image-20210408105100775](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210408105100775.png)

# Flask 变量规则

## Flask 变量规则

通过向规则参数添加变量部分，可以动态构建URL。此变量部分标记为**<variable-name>** 。它作为关键字参数传递给与规则相关联的函数。

在以下示例中，**route()**装饰器的规则参数包含附加到URL **'/hello'** 的**<name>。** 因此，如果在浏览器中输入**http://localhost:5000/hello/w3cschool**作为**URL**，则**'w3cschool'**将作为参数提供给 **hello()**函数。

```python
from flask import Flask
app = Flask(__name__)

@app.route('/hello/<name>')
def hello_name(name):
   return 'Hello %s!' % name

if __name__ == '__main__':
   app.run(debug = True)
```

将上述脚本保存为**hello.py**并从Python shell运行它。接下来，打开浏览器并输入URL **http:// localhost:5000/hello/w3cschool。**

以下输出将显示在浏览器中:

```python
Hello w3cschool!
```

# Flask URL构建

## **Flask URL构建**

**url_for()**函数对于动态构建特定函数的URL非常有用。该函数接受函数的名称作为第一个参数，以及一个或多个关键字参数，每个参数对应于URL的变量部分。

以下脚本演示了如何使用**url_for()**函数：          url_for()反向解析

```python
from flask import Flask, redirect, url_for
app = Flask(__name__)
@app.route('/admin')
def hello_admin():
   return 'Hello Admin'


@app.route('/guest/<guest>')

def hello_guest(guest):
   return 'Hello %s as Guest' % guest


@app.route('/user/<name>')
def hello_user(name):
   if name =='admin':
      return redirect(url_for('hello_admin'))
   else:
      return redirect(url_for('hello_guest',guest = name))


if __name__ == '__main__':
   app.run(debug = True)
```

# Flask 模板

## 模板变量

代码中传入字符串，列表，字典到模板中

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    # 往模板中传入的数据
    my_str = 'Hello Word'
    my_int = 10
    my_array = [3, 4, 2, 1, 7, 9]
    my_dict = {
        'name': 'xiaoming',
        'age': 18
    }
    return render_template('hello.html',
                           my_str=my_str,
                           my_int=my_int,
                           my_array=my_array,
                           my_dict=my_dict
                           )
```

模板中代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
  我的模板html内容
  <br />{{ my_str }}
  <br />{{ my_int }}
  <br />{{ my_array }}
  <br />{{ my_dict }}
</body>
</html>
```

# Flask 静态文件

## Flask 静态文件

Web应用程序通常需要静态文件，例如**javascript**文件或支持网页显示的**CSS**文件。通常，配置Web服务器并为您提供这些服务，但在开发过程中，这些文件是从您的包或模块旁边的*static*文件夹中提供，它将在应用程序的**/static**中提供。

特殊端点'static'用于生成静态文件的URL。

在下面的示例中，在**index.html**中的HTML按钮的**OnClick**事件上调用**hello.js**中定义的**javascript**函数，该函数在Flask应用程序的**“/”**URL上呈现。

```python
from flask import Flask, render_template
app = Flask(__name__)

@app.route("/")
def index():
   return render_template("index.html")

if __name__ == '__main__':
   app.run(debug = True)
```

**index.html**的HTML脚本如下所示：

```html
<html>

   <head>
      <script type = "text/javascript" 
         src = "{{ url_for('static', filename = 'hello.js') }}" ></script>
   </head>
   
   <body>
      <input type = "button" onclick = "sayHello()" value = "Say Hello" />
   </body>
   
</html>
```

**hello.js**包含**sayHello()**函数。

```js
function sayHello() {
   alert("Hello World")
}
```

# Flask Request对象

来自客户端网页的数据作为全局请求对象发送到服务器。为了处理请求数据，应该从Flask模块导入。

Request对象的重要属性如下所列：

- **Form** - 它是一个字典对象，包含表单参数及其值的键和值对。
- **args** - 解析查询字符串的内容，它是问号（？）之后的URL的一部分。
- **Cookies** - 保存Cookie名称和值的字典对象。
- **files** - 与上传文件有关的数据。
- **method** - 当前请求方法。

# Flask 将表单数据发送到模板

html中的action可以理解为重定向

## Flask 将表单数据发送到模板

我们已经看到，可以在 URL 规则中指定 http 方法。触发函数接收的 **Form** 数据可以以字典对象的形式收集它并将其转发到模板以在相应的网页上呈现它。

在以下示例中，**'/' URL** 会呈现具有表单的网页（student.html）。填入的数据会发布到触发 **result()** 函数的 **'/result' URL**。

**result()** 函数收集字典对象中的 **request.form** 中存在的表单数据，并将其发送给 **result.html**。

该模板动态呈现**表单**数据的 HTML 表格。

下面给出的是应用程序的 Python 代码：

```python
from flask import Flask, render_template, request
app = Flask(__name__)
@app.route('/')
def student():
   return render_template('student.html')


@app.route('/result',methods = ['POST', 'GET'])
def result():
   if request.method == 'POST':
      result = request.form
      return render_template("result.html",result = result)


if __name__ == '__main__':
   app.run(debug = True)
```

```html
 下面给出的是 student.html 的 HTML 脚本。
<form action="http://localhost:5000/result" method="POST">
     <p>Name <input type = "text" name = "Name" /></p>
     <p>Physics <input type = "text" name = "Physics" /></p>
     <p>Chemistry <input type = "text" name = "chemistry" /></p>
     <p>Maths <input type ="text" name = "Mathematics" /></p>
     <p><input type = "submit" value = "submit" /></p>
  </form>
```

下面给出了模板**（ result.html ）**的代码：

```html
<!doctype html>
  <table border = 1>
     {% for key, value in result.items() %}
    <tr>
       <th> {{ key }} </th>
       <td> {{ value }}</td>
    </tr>
 {% endfor %}
</table>
```

# 变量规则

```python
from markupsafe import escape

@app.route('/user/<username>')
def show_user_profile(username):
    # show the user profile for that user
    return 'User %s' % escape(username)

@app.route('/post/<int:post_id>')
def show_post(post_id):
    # show the post with the given id, the id is an integer
    return 'Post %d' % post_id

@app.route('/path/<path:subpath>')
def show_subpath(subpath):
    # show the subpath after /path/
    return 'Subpath %s' % escape(subpath)
```

转换器类型：

| `string` | （缺省值） 接受任何不包含斜杠的文本 |
| -------- | ----------------------------------- |
| `int`    | 接受正整数                          |
| `float`  | 接受正浮点数                        |
| `path`   | 类似 `string` ，但可以包含斜杠      |
| `uuid`   | 接受 UUID 字符串                    |


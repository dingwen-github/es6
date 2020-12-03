# `ES6`

## Class & Object

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ClassAndObject</title>
</head>
<body>
<script>
    /*类*/
    class Star {
        /*构造函数*/
        constructor(name, age) {
            /*this 即为当前实例对象*/

            /*类的公有属性放在构造方法内*/
            this.name = name
            this.age = age
            /*构造函数返回当前对象*/
        }

        /*方法*/
        sing(song){
            console.log(this.name + song)
        }
    }

    let eason = new Star('陈奕迅',40)
    eason.sing('红玫瑰')
    console.log(eason)


</script>

</body>
</html>
```



## Extends 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Extends</title>
</head>
<body>
<button>dance</button>
<script>
    // 1. 在 ES6 中类没有变量提升，所以必须先定义类，才能通过类实例化对象
    // 2. 类里面的共有的属性和方法一定要加this使用.
    // 3. 谁调用this就指向谁

    let that;
    class Father {
        constructor(x, y) {
            console.log('father constructor')
            this.x = x;
            this.y = y;
        }

        money() {
            console.log('100$')
        }

        sum() {
            console.log(this.x + this.y)
        }
        say(){
            console.log('father hello')
        }
    }

    class Son extends Father {

        /* 默认存在，必须调用super*/
        // constructor 里面的this 指向的是 创建的实例对象
        constructor(x,y){
            super(x, y);
            this.x = x;
            this.y = y;
            this.btn = document.querySelector('button')
            this.btn.onclick = this.dance
            that = this;

        }

        // 继承中的属性或者方法查找原则: 就近原则
        // 1. 继承中,如果实例化子类输出一个方法,先看子类有没有这个方法,如果有就先执行子类的
        // 2. 继承中,如果子类里面没有,就去查找父类有没有这个方法,如果有,就执行父类的这个方法(就近原则)
        say(){
            console.log(' son hello')
        }

        /*子类拓展方法*/
        subtract(){
            console.log(this.x - this.y)
        }

        dance(){
            //此处的this,指的是btn
            console.log(this)
            console.log(that)
        }
    }

    let xm = new Son(100, 200);
    xm.money();
    xm.sum();
    xm.say()
    xm.subtract()
</script>
</body>
</html>
```
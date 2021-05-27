```
class Animal{
		constructor(x,y){
			this.x=x
			this.y=y
		}
		sum(){
			return this.x+this.y
		}
	}
	class Human extends Animal{
		constructor(x,y,z){
			super(x,y)  //继承父类的this
			this.z=z
		}
		sum(){
			return this.z+super.sum() //调用父类的this
		}
	}

	let person=new Human(2,3,3)
```

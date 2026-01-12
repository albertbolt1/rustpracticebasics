# rustpracticebasics


<b> 
Everything depends on being able tp prove that parallelism and all are safe at compile time and that also carries forward to the run time
</b>

For practising rust basics and also noting down important points

<br>
Data with an unknown size at compile time or a size that might change must be stored on the heap instead.
<br>
The main purpose of ownership is to manage heap data can help explain why it works the way it does.
<br>
Rust
fn main()
{
let a = 10;
let b = Box::new(20);
let c = 20;
}

stack 
c
b - pointer to heap memory
a

<br>
after main ends the drop of b will be called and it will be removed from heap memory, the stack slot is kinda dead? but what does that mean ?

Note: In C++, this pattern of deallocating resources at the end of an item’s lifetime is sometimes called Resource Acquisition Is Initialization (RAII). The drop function in Rust will be familiar to you if you’ve used RAII patterns.

<br>
<b> greatest concept of all time, ownership </b>
```
let s1 = String::from("hello");
let s2 = s1;
```
here what will happen is s1 and s2 will point to the same string on heap and when we go out of scope we would have to delete the same memory twice and this is an issue so we have the concept of ownership when we so s2 = s1, the ownsership of the object on heap passed to s2 and s1 cannot be used any more, this way when we go out of scope the object will be only deleted once 

This is known as a <b>"move"</b> 

check how move work with unique_ptr an shared_ptr in c++

<br>
clone in rust creates copy of object on the heap
```
let s1 = String::from("hello");
let s2 = s1.clone();
println!("s1 = {s1}, s2 = {s2}");
```
<img src="https://doc.rust-lang.org/book/img/trpl04-03.svg" height="500px" width="500px"/>
it would clone stack and heap entry both 


Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type for the life of that reference.

We’re not allowed to modify something we have a reference to.

<b> If we use &something then something here becomes immutable or read only, we wont be able to change anything, if we want to change something then we would need mutable reference &mut something </b> 
<b> Rust ensures that we have many immutable references ie read or one mutable reference but not both and not many mutable references as that can also cause data races </b>


traits are like interfaces



 

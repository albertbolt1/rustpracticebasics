```
// Given a list of integers, use a vector and return the median (when sorted, the value in
// the middle position) and mode (the value that occurs most often; a hash map will be
// helpful here) of the list

use std::collections::HashMap;
fn main() {

 let mut arr =  vec![4,5,12,3,78,90,12,15,15,15];
 // sort the array
 arr.sort();
 
 // create an hash map 
 let mut hashmap = HashMap::new();
 
 let mut mode = -1;
 let mut max_count = 0;
 
 for &i in &arr {
    let count = hashmap.entry(i).or_insert(0);
    *count+=1;
    if *count > max_count 
    {
        mode = i;
        max_count = *count;
    }
 }
 
 println!("mode of the array is {}",mode);
}
```
```
// Convert strings to Pig Latin. The first consonant of each word 
// is moved to the end of the word and ay is added, so first becomes irst-fay. 
// Words that start with a vowel have hay added to the end 
// instead (apple becomes apple-hay). Keep in mind the details about UTF-8 encoding!

fn main() {

let vowels = vec!['a','e','i','o','u'];

let mut given_string = String::from("apple");
let mut given_another_string = String::from("first");

convert_to_piglatin(&mut given_string,&vowels);
convert_to_piglatin(&mut given_another_string,&vowels);

println!("{}",given_string);
println!("{}",given_another_string);

}

pub fn convert_to_piglatin(given: &mut String,arr: &Vec<char>)
{
        if arr.contains(&given.chars().next().unwrap()) 
        {
            given.push_str("-hay");
        }
        else
        {
        let first = given.chars().next().unwrap();
        let mut rest: String = given.chars().skip(1).collect();
        
            rest.push(first);
            rest.push_str("-ay");
            *given=rest;
        }
}
```

## Teaching myself Computer Science - Data Structures: Array

### Backstory

I'm working as a developer for 7 years. I managed to find jobs so far without a degree and with no knowledge of computer science fundamentals. Now I'm thinking of a job change and the companies I want to work for need strong CS knowledge. There is no way around it. So I'm going to focus on improving my CS knowledge in 2021 and 2022 (if it takes that long).

It is a long shot and I am aware that I might lose motivation and stop. Doing this in Rust, and blogging about my progress is to keep it interesting and to keep doing it as long as possible. Even if I fail, I will gain something and will be better than where I am now.

There are not many resources for implementing data structures and algorithms in Rust. I guess Rust makes it hard to implement any of those because of its safety mechanisms. But personally, Rust is fascinating. It has unique solutions to some of the common problems in other languages. So I decided to go with rust despite some good advice against doing so for this particular use case.

### Array

An array is a collection of equal-sized data, stored in a contiguous memory location, and indexed by contiguous integers. The contiguous and equal-sized split are important characteristics. We refer to the memory address of the array's first element and other element's positions can be calculated by simple arithmetic operations.

This makes random access possible, which means we can read from any position of the array without increasing the complexity. Read operation is O(1) regardless of the size of the array. Array also provides constant-time access O(1) when you want to add an element at the end of an array.

Both reading from an array and adding an element at last (push) are constant-time access because calculating the address is just some arithmetic operations. Similarly, removing the last element from an array (pop) is O(1) complexity.

Things get interesting when you want to add or remove an element in any arbitrary position of an array. That's possible but that is O(N) operation. Any operation we want to do in an arbitrary position of an array is complex.

- When inserting an element in an arbitrary position, the current element in that position has to be moved to make room for the new one. The whole array has to be re-adjusted from the point of insertion to the last element.
- When removing, the element will be removed and the next element (index + 1) has to be moved to its position, and the whole array has to be readjusted till the end.

That's enough of theory. Now let's see a bare-bones implementation of an array in rust. The following are the operations that need to be supported for minimal array implementation. This list is not exhaustive.

- Adding new element - Push
- Removing last element - Pop
- Reading element at index - Get
- Add element at index - Insert At
- Delete the element at index - Delete At

### Implementation

#### Test
This is the first time ever I am writing tests in rust and also starting with TDD. It is a good feeling to make a failing test pass.

```
mod ds_tests {
    use super::ds;

    #[test]
    fn add_elements_to_array() {
        let data: Vec<i32> = vec![];
        let mut arr = ds::Array::new(0, data);
        arr.push(8);
        arr.push(18);
        assert_eq!(arr.length, 2);
    }
    #[test]
    fn remove_element_from_array() {
        let data: Vec<i32> = vec![1, 4, 5];
        let mut arr = ds::Array::new(0, data);
        arr.pop();
        assert_eq!(arr.length, 2);
    }
    #[test]
    fn get_element_at_index() {
        let data: Vec<i32> = vec![1,2,5];
        let arr = ds::Array::new(0, data);
        let value = arr.get_element(1);
        assert_eq!(*value, 2);
    }
    #[test]
    fn insert_element_at_index() {
        let data: Vec<i32> = vec![1,2,5];
        let mut arr = ds::Array::new(0, data);
        arr.insert_at(1, 42);
        assert_eq!(*arr.get_element(1), 42);
    }
    #[test]
    fn delete_element_at_index() {
        let data: Vec<i32> = vec![1,2,5];
        let mut arr = ds::Array::new(0, data);
        arr.delete_at(1);
        assert_ne!(*arr.get_element(1), 2);
    }
}
```
#### Array
```
mod ds {
    pub struct Array<T> {
        pub length: usize,
        data: Vec<T>,
    }
    impl<T: Clone> Array<T> {
        pub fn new(length: usize, data: Vec<T>)-> Array<T> {
            return Array { length, data};
        }
        pub fn push(&mut self, elem: T) {
            self.data.push(elem);
            self.calculate_length();
        }
        pub fn pop(&mut self) {
            self.data.pop();
            self.calculate_length();
        }
        pub fn get_element(&self, index: usize)-> &T {
            return &self.data[index];
        }
        pub fn insert_at(&mut self, index: usize, new_element: T) {
            let mut data: Vec<T> = vec![];
            for (position, element) in self.data.iter().enumerate() {
                if position == index {
                    data.push(new_element.clone());
                }
                data.push(element.clone());
            }
            self.data = data;
            self.calculate_length();
        }
        pub fn delete_at(&mut self, index: usize){
            let mut data: Vec<T> = vec![];
            for (position, elem) in self.data.iter().enumerate() {
                if position != index {
                    data.push(elem.clone());
                }
            }
            self.data = data;
            self.calculate_length();
        }
        fn calculate_length(&mut self) {
            self.length = self.data.len();
        }

    }
}
```

### What's next

- Multi-dimensional array.
- Amortised cost and 
- Jagged array (Array of Arrays).
- Implementing without using the built-in Array in rust.
- Implementing fixed-length arrays.
- implementing overflow and underflow conditions.
- Amortized cost and array expanding strategy (dynamic arrays).

---

#### Update 1:

> Array also provides constant-time access O(1) when you want to add an element at the end of an array.

[/u/Nokel81](https://www.reddit.com/user/Nokel81/) pointed out that the above statement is incorrect for dynamic arrays without defined capacity. That's because the arrays have to be resized when they're full to accommodate new elements. That's not an O(1) operation. But generally, it is considered as O(1) of amortized cost. More on the amortization in a later blog post, I need to understand the amortized cost analysis methods better before writing it.

---

Thanks for reading so far. I have no clue how hard or possible it is to implement the above in rust. I'll do some attempts and see where that leads. Please share any feedback, I would really appreciate it. You can consider me a noob in CS fundamentals.
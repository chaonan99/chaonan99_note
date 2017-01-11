## Memory Networks
* [paper link](http://arxiv.org/abs/1410.3916v11)

### Structure
* **I(input feature map)**
    + Standard pre-processing, e.g., parsing, co reference and entity resolution for text inputs
* **G(generalization)**
    + Simplest form: ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bm%7D_%7BH%28x%29%7D%3DI%28x%29) store ![equation](http://latex.codecogs.com/svg.latex?I%28x%29) to a slot of memory.
    + More sophisticated form: update all ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bm%7D) based on `x`
* **O(output feature map)**
    + Find relevant memories
* **R(response)**
    + Procedure the final response given `o`

### Procedure
1. Convert `x` to an internal feature representation `I(x)`
2. Update memories ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bm%7D_i) given the new input: ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bm%7D_i%20%3D%20G%28%5Cmathbf%7Bm%7D_i%2CI%28x%29%2C%5Cmathbf%7Bm%7D%29) for all `i`
3. Compute output features `o` given the new input and the memory: ![equation](http://latex.codecogs.com/svg.latex?o%20%3D%20O%28I%28x%29%2C%5Cmathbf%7Bm%7D%29)
4. Finally, decode output features `o` to give the final response: ![equation](http://latex.codecogs.com/svg.latex?r%20%3D%20R%28o%29)

### Use MemNN on Q&A task
#### Basic model
+ `I` = input text (sentence or word-based)
+ `G` = store new text into the next memory (![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bm%7D_N%3Dx%2C%20N%3DN%2B1))
+ `O` = finding ![equation](http://latex.codecogs.com/svg.latex?k) relevant memories (they try ![equation](http://latex.codecogs.com/svg.latex?k%3D1%2C2))
![equation](http://latex.codecogs.com/svg.latex?o_1%3DO_1%28x%2C%5Cmathbf%7Bm%7D%29%3D%5Cmathop%7B%5Carg%5Cmax%7D%20%5Climits_%7Bi%3D1%2C2%2C...%2CN%7Ds_O%28x%2C%5Cmathbf%7Bm%7D_i%29)
![equation](http://latex.codecogs.com/svg.latex?o_2%3DO_2%28x%2C%5Cmathbf%7Bm%7D%29%3D%5Cmathop%7B%5Carg%5Cmax%7D%20%5Climits_%7Bi%3D1%2C2%2C...%2CN%7Ds_O%28%5Bx%2C%5Cmathbf%7Bm%7D_%7Bo_1%7D%5D%2C%5Cmathbf%7Bm%7D_i%29)
+ `R` = produce a textual response `r`
    * Return ![equation](http://latex.codecogs.com/svg.latex?%5Cmathbf%7Bm%7D_%7Bo_k%7D) (the last retrieved sentence)
    * Use RNN to generate text
    * Return single word by ranking them:
    ![equation](http://latex.codecogs.com/svg.latex?r%3D%5Carg%5Cmax_%7B%5Comega%20%5Cin%20W%7Ds_R%28%5Bx%2C%5Cmathbf%7Bm%7D_%7Bo_1%7D%2C%5Cmathbf%7Bm%7D_%7Bo_2%7D%5D%2C%5Comega%29)
+ Score function in `O` and `R` (![equation](http://latex.codecogs.com/svg.latex?s_O%2C%20s_R))
![equation](http://latex.codecogs.com/svg.latex?s%28x%2C%20y%29%20%3D%20%20%5CPhi_x%28x%29%5E%7B%5Cmathbf%7BT%7D%7DU%5E%7B%5Cmathbf%7BT%7D%7DU%5CPhi_y%28y%29)
where ![equation](http://latex.codecogs.com/svg.latex?%5CPhi_x%2C%20%5CPhi_y) map original text to the D-dimensional feature space and ![equation](http://latex.codecogs.com/svg.latex?U) is the embedding matrix, ![equation](http://latex.codecogs.com/svg.latex?U%5Cin%5Cmathbb%7BR%7D%5E%7Bn%5Ctimes%20D%7D)
+ Training
    * loss function
    ![2016_09_15_868e7f2723d58af0b4287e94e345b8c7](http://oa5omjl18.bkt.clouddn.com/2016_09_15_868e7f2723d58af0b4287e94e345b8c7.png "Add Description")
    * Intuition: make ![equation](http://latex.codecogs.com/svg.latex?s_O%28x%2C%5Cmathbf%7Bm%7D_%7Bo_1%7D%29) larger than all ![equation](http://latex.codecogs.com/svg.latex?s_O%28x%2C%5Cbar%7Bf%7D%29) for at least ![equation](http://latex.codecogs.com/svg.latex?%5Cgamma).



<p>control flow</p>

基本流程控制三個指令 pass, continue, break  
pass: 執行另一個區塊, 所以通常會搭配if...else, 所以在位置1.時無實質功能, 2.表示當i被2整除時, 會執行else  
continue: 當執行到這一行時, 開始下一個for迴圈, 所以3.表示i小於10時, 直接跳到for迴圈開始下一個i, 不會到達print  
break: 當執行到這一行時, 終止if/整個for迴圈, 因此當i大於10時, 會直接跳出for迴圈, 不會到達print  



        print("start")
        for i in range(50):
            pass # 1.
            if i % 2 == 0:
                pass # 2.
            else:
                if i < 10:
                    continue # 3.
                if i > 10:
                    break # 4.
            print(i) # 注意縮排的位置
        print("end")


輸出結果:

start
0
2
4
6
8
10
end

<p>activation function</p>

linear: f(x) = x, -inf to inf

sigmoid: f(x) = 1/(1+e^x), 0 to 1
tanh: , -1 to 1
relu: max(0, x), 0 to inf
leak relu: 
       
Magic Method
__new__
__init__
__call__
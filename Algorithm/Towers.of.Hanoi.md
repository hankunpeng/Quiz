# 河内塔


河内塔「Towers of Hanoi」是法国人 M.Claus「Lucas」于 1883 年从泰国带到法国的，河内为越战时北越的首都，即现在的胡志明市区。1883 年法国数学家 Edouard Lucas 曾提及这个故事，据说创世纪时 Benares 有一座塔是由三支钻石棒所支撑，开始时神在第一根棒上放置 64 个由上至下依由小到大排列的金盘，并命令僧侣将所有的金盘从第一根棒移至第三根棒，且搬运过程中遵守大盘子在小盘子之下的原则，若每日仅搬运一个盘子，则当盘子全数搬运完毕之日，就是世界末日降临之时。


## 算法题目
有 A、B、C 三根柱子，A 柱由上至下放置了 n 个按由小到大排列圆环。
现在要把所有圆环从 A 柱移至 C 柱，B 柱为辅助柱，搬运过程中遵守大环在小环之下的原则。
假设 n == 8 ，请设计移动算法并打印出移动步骤。


## 参考答案

- C 代码
```
#include <stdio.h>

void hanoi(int n, char A, char B, char C) {
    if(n == 1) {
        printf("圆环从 %c 移至 %c\n", A, C);
    }
    else {
        hanoi(n-1, A, C, B);
        hanoi(1, A, B, C);
        hanoi(n-1, B, A, C);
    }
}

int main() {
    int n;
    printf("请输入圆环数：");
    scanf("%d", &n);
    hanoi(n, 'A', 'B', 'C');
    return 0;
} 
```

- Java 代码
```
import java.util.*;
import static java.lang.System.out;

public class Hanoi {
    static class Move {
        char from, to;
        Move(char from, char to) {
            this.from = from;
            this.to = to;
        }
    }
	
    List<Move> solve(int n) {
        moves = new ArrayList<Move>();
        move(n, 'A', 'B', 'C');
        return moves;
    }

    private List<Move> moves;
	
    private void move(int n, char a, char b, char c) {
        if(n == 1) {
            moves.add(new Move(a, c));
        } else {
            move(n - 1, a, c, b); 
            move(1, a, b, c); 
            move(n - 1, b, a, c);
        }
    }
    
    public static void main(String args[]) {
        out.print("请输入圆环数：");
        Hanoi hanoi = new Hanoi();
        int n = new Scanner(System.in).nextInt();
        for(Move move : hanoi.solve(n)) {
            out.printf("圆环从 %c 移至 %c%n", move.from, move.to);
        }
    }
}
```



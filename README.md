# interviewbit--maths--find-nth-fibonacci

**----> Question:**

Given an integer A you need to find the Ath fibonacci number modulo 109 + 7.

The first fibonacci number F1 = 1

The first fibonacci number F2 = 1

The nth fibonacci number Fn = Fn-1 + Fn-2 (n > 2)



Problem Constraints
1 <= A <= 109.



Input Format
First argument is an integer A.



Output Format
Return a single integer denoting Ath fibonacci number modulo 109 + 7.



Example Input
Input 1:

 A = 4
Input 2:

 A = 3


Example Output
Output 1:

 3
Output 2:

 2


Example Explanation
Explanation 1:

 F3 = F2 + F1 = 1 + 1 = 2
 F4 = F3 + F2 = 2 + 1 = 3
Explanation 2:

 F3 = F2 + F1 = 1 + 1 = 2
 
 
**-----> Code:**
 
 void multi(long long int m[2][2],long long int f[2][2]){
 
    long long int x= ((m[0][0]*f[0][0])%1000000007+(m[0][1]*f[1][0])%1000000007)%1000000007;
    long long int y= ((m[0][0]*f[0][1])%1000000007+(m[0][1]*f[1][1])%1000000007)%1000000007;
    long long int z= ((m[1][0]*f[0][0])%1000000007+(m[1][1]*f[1][0])%1000000007)%1000000007;
    long long int a= ((m[1][0]*f[0][1])%1000000007+(m[1][1]*f[1][1])%1000000007)%1000000007;

    m[0][0]=x;
    m[0][1]=y;
    m[1][0]=z;
    m[1][1]=a;
}

void power(long long int m[2][2],int n){

    if(n == 1)
       return;
   
    long long int f[2][2] = {{1, 1}, {1, 0}};
     
    power(m, n / 2);
    multi(m, m);
     
    if (n % 2 != 0)
        multi(m, f);
}

int Solution::solve(int A) {
   
    long long int m[2][2]={{1,1},{1,0}};
    power(m,A-1);    
    return m[0][0];
}

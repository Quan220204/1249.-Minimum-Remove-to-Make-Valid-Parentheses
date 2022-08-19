# 1249.-Minimum-Remove-to-Make-Valid-Parentheses
Leetcode exercise

Given a string s of '(' , ')' and lowercase English characters.
Your task is to remove the minimum number of parentheses ( '(' or ')', in any positions ) so that the resulting
parentheses string is valid and return any valid string.

Formally, a parentheses string is valid if and only if:
It is the empty string, contains only lowercase characters, or
It can be written as AB (A concatenated with B), where A and B are valid strings, or
It can be written as (A), where A is a valid string.
 
Example 1:
Input: s = "lee(t(c)o)de)"
Output: "lee(t(c)o)de"
Explanation: "lee(t(co)de)" , "lee(t(c)ode)" would also be accepted.

Example 2:
Input: s = "a)b(c)d"
Output: "ab(c)d"

Example 3:
Input: s = "))(("
Output: ""
Explanation: An empty string is also valid.
 
Constraints:
1 <= s.length <= 105
s[i] is either'(' , ')', or lowercase English letter.

     
     
      The idea here is quite natural that the extra ")" while traversing the string will turn into " ". To do 
      this, I convert the string to a list.After the for loop, if there is still a sign "(" in the stack, it
      means that in the string there are excess signs "(", I gradually delete these signs in the list).
      Finally I convert the list to a string.
      
      class Solution:
          def minRemoveToMakeValid(self, s: str) -> str:
             S = list(s)
             stack = []
             n = len(s)
             for i in range(0, n):
                 if S[i] == "(":
                    stack.append(S[i])
                 elif S[i] == ")":
                    if stack:
                      stack.pop()
                    else:
                      S[i]=""
             m=len(stack)
             for i in range(0,n):
                 if m>0 and S[n-i-1]=='(':
                    S[n-1-i] = ""
                     m-=1
             return "".join(S)

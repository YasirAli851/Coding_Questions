Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

 

Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
 

Constraints:

1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters.



---------------------X--------------------X--------------------------------------



LINK TO QUESTION:-https://leetcode.com/problems/longest-common-prefix/

MY LEETCODE SUBMITTED SOLUTION:-

class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        
    if(strs.size()==1)
    {
        string s=strs[0];
        return s;
    }
    else
    {
       int k=0;
       string result;
       int trc=0;
       for(int i=0;i<strs[0].size();i++)
       {
          int con=0;
          int check=1;
          char c=strs[0][i];
          for(int j=1;j<strs.size();j++)
          {
              if(strs[j][i]==c)
              {
                check++;
              }
              else
              {
                con++;
                break;
              }
          }
          if(con!=0)
          {
             break;
          }
          else
          {
              if(check==strs.size())
              {
                 trc++;
                 result+=c;
               }
           }
       }
       if(trc!=0)
       {
          return result;
       }
       else
       {
         string s="";
         return s;
       }
    }
        
  }
};

MY CODE BELOW WITH EXPLANATION(PLEASE REFER VOID SOLVE FUNCTION):-


/*Yasir Ali*/
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
#include <sstream>
#include <queue>
#include <deque>
#include <bitset>
#include <iterator>
#include <list>
#include <stack>
#include <map>
#include <set>
#include <functional>
#include <numeric>
#include <utility>
#include <limits>
#include <time.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
using namespace std;
#define nl "\n"
#define ll long long
#define sz length()
#define PI 3.1415926535897932384626433832795
#define MOD 1000000007
#define FOR(i,a,b) for(ll i=a;i<=b;i++)
const ll INF=1e9+7;
bool isPrime(ll x)
{
   bool check=true;
   for(ll i=2;i<x;i++)
   {
      if(x%i==0)
      {
         check=false;
         break;
      }
   }
   if(check && x!=1)
   {
      return true;
   }
   else
   {
      return false;
   }
}

//To take space separated string
 // while (true)
 //    {
 //      cin>>z;
 //      s+=z;
 //      if(cin.peek()=='\n')
 //      break;
 //    }

ll gcd(ll x,ll y)
{
   int final=-1;
   for(int i=2;i<x || i<y;i++)
   {
      if(x%i==0 && y%i==0)
      {
         final=i;
      }
   }
   return final;
}
void removeSpaces(string &str)
{
    int n = str.length();
    int i = 0, j = -1;
    bool spaceFound = false;
    while (++j < n && str[j] == ' ');
    while (j < n)
    {
        if (str[j] != ' ')
        {
            
            if ((str[j] == '.' || str[j] == ',' ||
                 str[j] == '?') && i - 1 >= 0 &&
                 str[i - 1] == ' ')
                str[i - 1] = str[j++];
 
            else
               
                str[i++] = str[j++];
 
           
            spaceFound = false;
        }
        else if (str[j++] == ' ')
        {
            
            if (!spaceFound)
            {
                str[i++] = ' ';
                spaceFound = true;
            }
        }
    }
    if (i <= 1)
        str.erase(str.begin() + i, str.end());
    else
        str.erase(str.begin() + i - 1, str.end());
}
void solve() 
{
   vector<string>vec;
   for(int i=0;i<3;i++)
   {
    string s;
    cin>>s;
    vec.push_back(s);
   }
   string result; //This string will store the longest common prefix.

   //This loop means,it will start from zero and goes upto last character of 
   //first string of vector
   for(int i=0;i<vec[0].size();i++)  
   {
        int check=1; //This check will keep the track that whether the character at a given
        //position in each string is matching or not.if true,then it will be incremented.

        int con=0; //we will increment this con if we don't find same character in a particualar 
        // position of each string

        char c=vec[0][i]; //This is the base string that is first string and with
        //the help of this string,we will match for every character in each string
        //at each position(index). 
        for(int j=1;j<3;j++) //we have already considered 1st string above.so
        //so,we will start searching from the second string.    
        {
            if(vec[j][i]==c) //vec[j][i] means different string but position is same
            //as denoted by "i-th index".
            {
                check++; //this means,when the character in the j-th string 
                //at i-th index will match from first string's i-th index
                //then it will be incremented.
            }
            else
            {
                con++; //if character will not match continuously then we will
                // break from the loop and increment con so that after getting out 
                //of this loop we will be able to break from the outer loop also.
                break;
            }
        }
        if(con!=0)//this condition check that whether our con has incremented
        //or not,and if our con is incremented that means we have not found the 
        //required characters continuously.so,we will keep our program running
        //upto that point only and then break from the loop.
        {
            break;
        }
        else //if con==0 that we have contiously found the required characters.
        {
            if(check==vec.size()) // this condition shows that if the check is equals
            //to the size of the vector that means we have found the same characters
            //in all the string in a given position.
            {
                result+=c; //so,we will add that character in our result string.
                //in variable "c":=we have kept each character of first string
                //one by one.
            }
        }
       
   }
   cout<<result<<endl; //printing the result.
}  
int main()
{
  //#ifndef Yasir_Ali
  //freopen("input.txt","r",stdin); 
  //freopen("output.txt","w",stdout);  
  //#endif 
  int tt;
  cin>>tt;
   
  while(tt--)
  {
      solve();
  }
   clock_t start, end;
    start = clock();
    end = clock();
    double time_taken= double(end - start)/ double(CLOCKS_PER_SEC);
    cerr << "Execution time: " << time_taken<< " secs";
 
    return 0;

}
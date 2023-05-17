
# 132.-Palindrome-Partitioning-II-leet-code-




bool ispalindrome(string &str, int i, int j)
    {
        while(i<=j)
        {
            if(str[i]!=str[j])
            {
                return false;
            }
            i++;
            j--;
                
        }
        
        return true;
    }
    
    
    int solve(string &str, int i, int j, vector<int>&dp)
    {
        if(i>=j) return 0;
        
        if(ispalindrome(str, i, j)) return 0;
        
        if(dp[i]!=-1) return dp[i];
        
        int ans=INT_MAX;
        for(int k=i; k<j; k++)
        {
            int a,b;

            if(ispalindrome(str, i, k))//no need further partition required of left part
            {
                int a;
                if(dp[k+1]!=-1)  a=dp[k+1];
                else
                {
                    a=solve(str, k+1, j, dp);
                }
                int temp = 1+a;

                ans=min(ans,temp);
            }

        }
        return dp[i]=ans;
        
    }


    int minCut(string str) {

        vector<int>dp(str.size(),-1);



        int a=solve(str, 0, str.size()-1, dp);

        for(int i=0;i<dp.size();i++)
        {
            cout<<dp[i]<<" ";
        }

        return a;
        
    }

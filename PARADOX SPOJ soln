#include <bits/stdc++.h>
using namespace std;
#define fr(i,j,n)   for(lli i=j;i<(n);++i)
#define bk(i,j,n)   for(lli i=j;i>=n;--i)
#define pb push_back
#define m_p make_pair
#define Fs first
#define Sc second
#define endl "\n"
#define MOD 1000000001
#define run ios_base::sync_with_stdio(0);cin.tie(0);cout.tie(0)
#define ordered_set tree<ll , null_type, less<ll>, rb_tree_tag, tree_order_statistics_node_update>
typedef long long int lli;
typedef vector<int> vi;
typedef pair<int,int> pi;
typedef vector<lli> vl;
typedef pair<lli,lli> pl;
inline lli max(lli a,lli b){ return a>b?a:b;}
inline lli min(lli a,lli b){ return a<b?a:b;}

bool visited[1000000];
int cnt[100000];        // cnt containing how many false are there in the cycle 
vector<pi> gp[1000000]; // graph containing 
unordered_set<int> mp; /// set for storing elements in current connected components 
bool ans=true; 
void dfs(int s)
{
    visited[s]=true;
    fr(i,0,gp[s].size())
    {
        int val=gp[s][i].Fs,c=gp[s][i].Sc;
        if(visited[val])
        {
           if(mp.find(val)!=mp.end()&&((c==1&&(cnt[s]-cnt[val])%2==1)||(c==-1&&(cnt[s]-cnt[val])%2==0)))
           {
                ans=false;
                return;
           }
        }
        else
        {
            if(c==1)
                cnt[val]=cnt[s];
            else
                cnt[val]=cnt[s]+1;
            mp.insert(val);
            dfs(val);
        }
    }
}
int main()
{
    lli n;
    while(1)
    {
        cin>>n;
        if(n==0)
            break;
        ans=true;
        fr(i,1,n+1)
        {
            gp[i].clear();
            cnt[i]=0;
            visited[i]=false;
        }
        lli m;
        string s;
        fr(i,1,n+1)
        {
            cin>>m>>s;
            if(s=="true")
                gp[i].pb({m,1});
            else
                gp[i].pb({m,-1});
        }
        fr(i,1,n+1)
        {
            if(!visited[i])
            {
                mp.clear();
                mp.insert(i);
                cnt[i]=0;
                dfs(i);
            }
        }
        //show(cnt,n+1);
        if(!ans)
        {
            cout<<"PARADOX"<<endl;
        }
        else
            cout<<"NOT PARADOX"<<endl;
    }
    return 0;
}

# hello-world
#c++ solution for problem 558B - Amr and The Large Array codeforces
#include<bits/stdc++.h>
using namespace std;
int main()
{
    int n;
    cin>>n;
    int arr[n];
    map<int,int> left;
    map<int,int> right;
    map<int,int> count;
    map<int,int> diff;
    for(int i=0;i<n;i++)
    {
        cin>>arr[i];
    }
    for(int i=0;i<n;i++)
    {
        count[arr[i]]++;
        if(left[arr[i]]==0)
        {
            left[arr[i]]=i+1;
            right[arr[i]]=i+1;
        }
        else
        {
            right[arr[i]]=i+1;
        }
        diff[arr[i]]=right[arr[i]]-left[arr[i]];
    }
    int max=INT_MIN;
    for(map<int,int>::iterator it=count.begin(); it!=count.end(); ++it)
    {
        if(it->second>max)
        {
            max=it->second;
        }
    }
  //  cout<<max<<endl;
    int dif=INT_MAX,keep=0;
    for(int i=0;i<n;i++)
    {
        if(count[arr[i]]==max)
        {
            dif=min(diff[arr[i]],dif);
            //ep=i;
            //cout<<dif<<"  "<<keep<<endl;
        }
    }
    for(int i=0;i<n;i++)
    {
        if(diff[arr[i]]==dif&&count[arr[i]]==max)
        {
            cout<<left[arr[i]]<<" "<<right[arr[i]];
            break;
        }
    }
    //cout<<left[arr[keep]]<<" "<<right[arr[keep]];
    return 0;

}

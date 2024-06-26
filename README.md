#include<iostream>
#include<ctime>
using namespace std;
int tries=3;
string message= "you have three chances !";
void hang_man(char);
int checkguess(char,string,string&);


int main()
{
    char letter;
    string month;
    string months[]={
        "january",
        "february",
        "march",
        "april",
        "may",
        "june",
        "july",
        "august",
        "september",
        "october",
        "november",
        "december"
    };

     srand(time(NULL));
    int month_number=rand()%12;
    month=months[month_number];
  string hide_month(month.length(),'X');
  system("cls");
  while(tries !=0)
  {
hang_man('n');
cout<<"\t\t\t\tLife: "<<tries<<endl;
cout<<hide_month<<endl;
cout<<"\t\t\t\tGuess a letter: ";
cin>>letter;
system("cls");

if(checkguess(letter,month,hide_month)==0)
{
message="Incorrect letter!";
tries--;
}
else
{
    message="Nice! correct guess";
}

if(hide_month==month)
{
    message="you free";
    hang_man('f');
    cout<<"\t\t\t\tLife: "<<tries<<endl;
    cout<<"\t\t\t\tThe month is: "<<month<<endl;
   break;
}

  }
if(tries==0)
{
    message="you,re hanged";
    hang_man('h');
    cout<<"\t\t\t\tLife: "<<tries<<endl;
    cout<<"\t\t\t\tThe month is: "<<month<<endl;

}

return 0;
}

int checkguess(char guess,string real_month,string &hidden_month)
{
    int matches=0;
    int len=real_month.length();
    for(int i=0;i<len;i++)
    {
        if(guess==hidden_month[i])
        {
            return 0;
        }
        if(guess==real_month[i])
        {
            hidden_month[i]=guess;
            matches++;
        }
    }
    return matches;
}

void hang_man(char state)
{
    string head_string="|";
    string stage="=====";
    string liver="|";
    if(state=='f')
    {
        head_string=" ";
    }
    else if(state=='h')
    {
        stage="     ";
        liver="/";
    }
    cout<<"\t\t\t\t__"<<endl;
    cout<<"\t\t\t\t         "<<head_string<<"       |"<<endl;
    cout<<"\t\t\t\t         O       |"<<endl;
    cout<<"\t\t\t\t        / \\      |"<<"\t   "<<message<<endl;
    cout<<"\t\t\t\t         |       |"<<"\t    /"<<endl;
    cout<<"\t\t\t\t        / \\      |         O "<<endl;
    cout<<"\t\t\t\t     =="<<stage<<"===  |         / \\"<<endl;
    cout<<"\t\t\t\t      |      |   |     "<<liver<<"    |"<<endl;
    cout<<"\t\t\t\t      |      |   |     =   / \\"<<endl;
    cout<<"\t\t\t\t======================|=|=========";
 

}

# Patient-Management-system-linked-list
This project is based on topic "PATIENT MANAGEMENT SYSTEM" using linked list with help of concepts of classes, objects and data file handling. This project is capable of keeping records of patients that are admitted in hospital. 
// dsa project.cpp : Defines the entry point for the console application.
//
**CODE:**
#include "stdafx.h"
#include<iostream>
#include<stdlib.h>
#include<string>
using namespace std;

class Plist
{
private:
	struct node
	{
	string patient_name;
	int bed_num ;
	int phone;
	int age;
	int ward_n ;
	string ward ;
	node *next;
	node *prev;
	}*head;
public:
	Plist()
	{
	head=NULL;
	}
	void add_patient_record(int bn, string pn, string w, int wn, int ph, int a) {
    node *p, *q;
    q = new node;
    p = head;
    q->patient_name = pn;
    q->bed_num = bn;
    q->age = a;
    q->ward = w;
    q->phone = ph;
    q->ward_n = wn;

    if (head == NULL) 
	{
        q->next = NULL;
        q->prev = NULL;
        head = q;
    }
	else if (q->bed_num < p->bed_num) 
	{
        q->next = head;
        q->prev = NULL;
        head->prev = q;
        head = q;
    }
	else if (q->bed_num == p->bed_num) 
	{
        cout << "Patient with bed number " << bn << " already exists.\n";
        delete q;
        return;
    } 
	else 
	{
        while (p->next != NULL) 
		{
            if (q->bed_num == p->bed_num || (q->bed_num > p->bed_num && q->bed_num < p->next->bed_num)) 
			{
                cout << "Patient with bed number " << bn << " already exists.\n";
                delete q;
                return;
            }
            p = p->next;
        }

        // If the new patient has the highest bed number, add it at the end
        p->next = q;
        q->prev = p;
        q->next = NULL;
    }
}

	void traverse()
	{
	node *p;
	p=head;
	while(p!=NULL)
	{
		cout<<"\t*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*"<<endl<<endl;	
		cout<<"PATIENT NAME = "<<p->patient_name<<endl;
		cout<<"AGE = "<<p->age<<endl;
		cout<<"PHONE NUMBER = "<<p->phone<<endl;
		cout<<"WARD(MALE OR FEMALE) = "<<p->ward<<endl;
		cout<<"WARD NUMBER = "<<p->ward_n<<endl;
		cout<<"BED NUMBER = "<<p->bed_num<<endl;
		cout<<"\t*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*"<<endl<<endl;	
		p=p->next;
	}
	}
	void del_patient_record(int value) 
	{
    node *p, *temp;
    p = head;

    if (head == NULL) 
	{
        cout << "No Record\n";
    } else {
        while (p != NULL && p->bed_num != value) {
            temp = p;
            p = p->next;
        }

        if (p == NULL) 
		{
            cout << "Patient with bed number " << value << " not found.\n";
        } 
		else 
		{
            if (p == head) 
			{
                head = p->next;
                if (head != NULL) 
				{
                    head->prev = NULL;
                }
            } 
			else 
			{
                temp->next = p->next;
                if (p->next != NULL) 
				{
                    p->next->prev = temp;
                }
            }

            delete p;
            cout << "Patient with bed number " << value << " deleted successfully.\n";
        }
    }
}
	void login()
	{

		string u;
		string use="user";
		string pass ="123";
		do
		{
			cout<<endl<<endl<<endl<<endl;
		cout<<"\t*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*"<<endl<<endl;	
cout<<"\t******************* USERNAME ****************** "<<endl<<endl;
cout<<"\tENTER USERNAME = ";
cin>>u;
cout<<endl;
if(u=="user");
{
cout<<"\t******************* PASSWORD ******************"<<endl<<endl;
cout<<"\tENTER PASSWORD = ";
cin>>pass;
cout<<endl;
cout<<"\t*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*!*"<<endl<<endl;	
if(pass != "123")
{
	cout<<endl<<endl<<endl<<endl;
	cout<<"\t****##***##***##***##***##***##****##***##****"<<endl<<endl;
	cout<<"\t***##*********** LOGIN FAILED ************##*** "<<endl<<endl;
	cout<<"\t****##***##***##***##***##***##****##***##****"<<endl<<endl;
    cout<<"\t***##************ ACCESS DENIED **********##*** "<<endl<<endl;
    cout<<"\t****##***##***##***##***##***##****##***##****"<<endl<<endl;
}   
else
{
    cout<<endl<<endl<<endl<<endl;
    cout<<"\t**%**%**%**%**%**%**%**%**%**%**%**%**%**%**%**"<<endl<<endl;
    cout<<"\t**%****%****%** LOGIN SUCCESSFULLY ****%****%** "<<endl<<endl;
    cout<<"\t**%**%**%**%**%**%**%**%**%**%**%**%**%**%**%**"<<endl<<endl;
    cout<<"\t****%****%****%** ACCESS GRANTED ****%****%**** "<<endl<<endl;
    cout<<"\t**%**%**%**%**%**%**%**%**%**%**%**%**%**%**%**"<<endl<<endl;
    cout<<endl<<endl<<endl<<endl;
    cout<<endl<<endl<<endl<<endl;
}
} 
} 
while(pass!="123");
}
};

int _tmain(int argc, _TCHAR* argv[])
{
int a;
string p,u;
Plist pl;

cout<<"\t***********************************************"<<endl;
cout<<"\t***********************************************"<<endl<<endl;
cout<<"\t*******    PATIENT MANAGEMENT SYSTEM    *******"<<endl<<endl;
cout<<"\t*******    WELCOME TO LOGIN PAGE    ************"<<endl<<endl;
cout<<"\t***********************************************"<<endl;
cout<<"\t***********************************************"<<endl<<endl;
cout<<endl<<endl<<endl<<endl;
    
      pl.login();                  
            
	  
cout<<"\t***********************************************"<<endl;
cout<<"\t***********************************************"<<endl<<endl;
cout<<"\t*******    PATIENT MANAGEMENT SYSTEM    *******"<<endl<<endl;
cout<<"\t**************    WELCOME   ******************"<<endl<<endl;
cout<<"\t***********************************************"<<endl;
cout<<"\t***********************************************"<<endl<<endl;

do
{
cout<<" Enter your choice "<<endl<<endl;
cout<<" 1 - PRESS 1 To Enter Patient Name "<<endl;
cout<<" 2 - PRESS 2 To Delete Patient Record "<<endl;
cout<<" 3 - PRESS 3 To Show Full Patient List "<<endl;
cout<<" 4 - PRESS 4 To Exit "<<endl<<endl;
cin>>a;
while((a<1)||(a>4))
{
cout<<"\n Enter the valid choice"<<endl;
cin>>a;
cout<<endl;
}system("CLS");
switch(a)
{
case 1:
{
int y,l,o,a;
string name;
string dep;
cout<<" ----- TO INSERT PATIENT DATA ----- "<<endl<<endl;
cout<<" Enter Patient Name = ";
cin>>name;
cout<<" Enter Phone Number = ";
cin>>l;
cout<<" Enter Age = ";
cin>>a;
cout<<" Enter Ward(M/F) = ";
cin>>dep;
cout<<" Enter Ward Number = ";
cin>>o;
cout<<" Enter Patient Bed Number = ";
cin>>y;

pl.add_patient_record(y,name,dep,o,l,a);
cout<<endl;
break;
system("CLS");
}
case 2:
{
int z;
cout<<" ----- TO DELETE PATIENT DATA ----- "<<endl<<endl;
cout<<" Enter the Bed number Of patient "<<endl;
cin>>z;
pl.del_patient_record(z);
break;
system("CLS");
}
case 3:
{
cout<<endl;
cout<<" ----- TO DISPLAY Full Patient LIST ---- "<<endl;
cout<<"*************************************************"<<endl<<endl;
pl.traverse();
cout<<endl;
cout<<endl<<endl;
break;
system("CLS");
}
case 4:
{
exit(0);
break;
}
}
}
while((a>=1)&&(a<=4));
cout<<endl;
system("pause");
	return 0;
}



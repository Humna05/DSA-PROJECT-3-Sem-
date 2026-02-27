# DSA-PROJECT-3-Sem-
Subject and study session management syetem 
#include <iostream>
using namespace std;

struct subject{
    string title;
    string ISBN;
    string author;
    int edition;
};
class sub{
  private:
    subject subjects[1000];
    int count=0;
  public:
 void addSubject(){
        if(count>=1000){
            cout<<"Subject Limit Reached!  "<<endl;
            return;
    }
        cout<<"Enter Subject Title:  "<<endl;
        cin>>subjects[count].title;
        cout<<"Enter ISBN:  "<<endl;
        cin>>subjects[count].ISBN;
		cout<<"Enter Author Name:  "<<endl;
        cin>>subjects[count].author;
        cout<<"Enter Edition:  "<<endl;
        cin>>subjects[count].edition;
        count++;
        cout<<"Subject Added Successfully    "<<endl;
  }
 void printsubject(){
        if(count==0){
            cout<<"No Subjects Found   "<<endl;
            return;
       }
         for(int i=0; i<count; i++){
            cout<<"Title: "<<subjects[i].title<<endl;
            cout<<"ISBN: "<<subjects[i].ISBN<<endl;
            cout<<"Author: "<<subjects[i].author<<endl;
            cout<<"Edition: "<<subjects[i].edition<<endl;
       }
      }
 void searchSubject(string searchtitle){
        for(int i=0; i<count; i++){
            if(subjects[i].title==searchtitle){
                cout<<"Subject Found!  "<<endl;
                cout<<"Title: "<<subjects[i].title<<endl;
                cout<<"ISBN: "<<subjects[i].ISBN<<endl;
                cout<<"Author: "<<subjects[i].author<<endl;
                cout<<"Edition: "<<subjects[i].edition<<endl;
                return;
            }
        }
            cout<<"Subject Not Found     "<<endl;
   }
 void updatesubject(string updatetitle){
        for(int i=0; i<count; i++){
            if(subjects[i].title==updatetitle){
                cout<<"Enter New ISBN:   "<<endl;
                cin>>subjects[i].ISBN;
                cout<<"Enter New Author:  "<<endl;
                cin>>subjects[i].author;
                cout<<"Enter New Edition:  "<<endl;
                cin>>subjects[i].edition;
				cout<<"Subject Updated Successfully!   "<<endl;
                return;
        }
        }
         cout<<"Subject Not Found\n\n";
}
 void deletesubject(string deletetitle){
        for(int i=0; i<count; i++){
            if(subjects[i].title==deletetitle){
			for(int j=i; j<count-1; j++){
                    subjects[j]=subjects[j+1];
        }
		count--;
        cout<<"Subject Deleted Successfully!  "<<endl;
        return;
    }
   }
           cout<<"Subject Not Found!  "<<endl;
    }
};

struct session{
    string subjectName;
    int hours;
    session*link;
};
class study{
  private:
    session*start;
  public:
    study(){
        start=NULL;
   }
void addSession(){
        session*newSession=new session;
        cout<<"Enter Subject Name:   "<<endl;
        cin>>newSession->subjectName;
		 cout<<"Enter Study Hours:  "<<endl;
        cin>>newSession->hours;
            newSession->link=NULL;
     
	 if(start==NULL){
            start=newSession;
       }
        else{
            session*temp=start;
            while(temp->link!=NULL){
                temp=temp->link;
        }
            temp->link=newSession;
     }
       cout<<"Study Session Added Successfully!   "<<endl;
}
 void displaySchedule(){
        if(start==NULL){
            cout<<"No Study Sessions Found!  "<<endl;
            return;
        }
     session*temp=start;
        while(temp!=NULL){
            cout<<"Subject: "<<temp->subjectName<<endl;
            cout<<"Hours: "<<temp->hours<<endl;
                temp=temp->link;
       }
    }
 void deleteSession(string name){
        if(start==NULL){
            cout<<"No Sessions to Delete  "<<endl;
            return;
        }
          session*temp=start;
        session*prev=NULL;

        while(temp!=NULL && temp->subjectName!=name){
            prev=temp;
            temp=temp->link;
    }
       if(temp == NULL){
            cout<<"Session Not Found!  "<<endl;
            return;
    }
        if(prev==NULL){
            start=temp->link;
        }
         else{
            prev->link=temp->link;
    }
        delete temp;
        cout<<"Session Deleted Successfully!  "<<endl;
  }
 void updateHours(string name){
        session*temp=start;
           while(temp!=NULL){
            if(temp->subjectName==name){
                cout<<"Enter New Study Hours:  "<<endl;
                cin>>temp->hours;
                cout<<"Study Hours Updated Successfully!   "<<endl;
                return;
           }
            temp=temp->link;
    }
        cout<<"Session Not Found!   "<<endl;
    }
};

int main(){
    sub subjectSystem;
    study studySystem;
    int choice;
    string name;
     while(choice!=10){
	    cout<<"1.Add Subject  "<<endl;
        cout<<"2.Display Subjects   "<<endl;
        cout<<"3.Search Subject   "<<endl;
        cout<<"4.Update Subject   "<<endl;
        cout<<"5.Delete Subject   "<<endl;
        cout<<"6.Add Study Session   "<<endl;
        cout<<"7.Display Study Schedule   "<<endl;
        cout<<"8.Delete Study Session   "<<endl;
        cout<<"9.Update Study Hours   "<<endl;
        cout<<"10.Exit   "<<endl;
        cout<<"Enter Choice:   "<<endl;
		cin>>choice;
    switch(choice){
      case 1:
	  subjectSystem.addSubject();
      break;

      case 2:
	  subjectSystem.printsubject();
      break;

      case 3:
	  cout<<"Enter Title to Search:   "<<endl;
      cin>>name;
      subjectSystem.searchSubject(name);
      break;

      case 4:
	  cout<<"Enter Title to Update:   "<<endl;
      cin>>name;
      subjectSystem.updatesubject(name);
      break;

      case 5:
	  cout<<"Enter Title to Delete:   "<<endl;
      cin>>name;
      subjectSystem.deletesubject(name);
      break;

      case 6:
	  studySystem.addSession();
      break;

      case 7:
      studySystem.displaySchedule();
      break;

      case 8:
       cout<<"Enter Subject Name to Delete:  "<<endl;
       cin>>name;
       studySystem.deleteSession(name);
       break;

      case 9:
        cout<<"Enter Subject Name to Update:   "<<endl;
        cin>>name;
        studySystem.updateHours(name);
        break;

      case 10:
        cout<<"Exiting Program!  "<<endl;
        break;

      default:
        cout<<"Invalid Choice!   "<<endl;
    }
 }
   return 0;
}

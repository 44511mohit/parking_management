# parking_management


#include <iostream>
#include<string>
#include <ctime>

using namespace std;

class Vehicle {
private:
    string cName;
    int vNumber;

public:
    Vehicle(string cName = "", int vNumber = 0) : cName(cName), vNumber(vNumber) {}

    void getData() {
        cout << "ENTER VEHICLE OWNNER NAME : ";
        cin >> cName;
        cout << "ENTER VEHICLE NO. : ";
        cin >> vNumber;
    }

    void displayData() const {
        cout<<"\t\t*****************************************"<<endl<<endl;
        cout<<"\t\t-------------PRIVATE-PARKING-------------"<<endl;
        cout<<"\t\t                             RECEIPT:"<<gen() <<endl;
       // cout<<"\t\tVEHICLE NUMBER : " << vNumber << endl<<endl;
        cout<<"\t\tVEHICLE OWNNER NAME : " << cName << endl;
        cout<<"\t\tVEHICLE NUMBER : " << vNumber << endl<<endl;
        
      //  cout<<"\t\treceipt "<<gen() <<endl;
    }
    static int gen() {
        static int receiptNumber = 0;
    return ++receiptNumber;
    }

    
};

class VEntryTime : public Vehicle {
private:
    time_t entryTime;

public:
    VEntryTime(string cName = "", int vNumber = 0) : Vehicle(cName, vNumber) {
        time(&entryTime);
    }


    void displayTime() const {
        displayData();
        cout << "\t\tEntry Time: " << ctime(&entryTime)<<endl;
       //  cout<<"\t\t***************************************"<<endl;
        cout<<"\t\t*****************************************"<<endl; 
    }
    
};

int main() {
    int value, bike = 0, car = 0, bus = 0;

    bool Exit=true;
    while(Exit) {
       cout<<"\n\t_________________________________________"<<endl;
       cout<<"\t  |      -> 1. Enter the BIKE         | "<<endl;
       cout<<"\t  |      -> 2. Enter the CAR          | "<<endl;
       cout<<"\t  |      -> 3. Enter the BUS          | "<<endl;
       cout<<"\t  |      -> 4. Total DATA             | "<<endl;
       cout<<"\t  |      -> 5. All DATA Remove        | "<<endl;
       cout<<"\t  |      -> 6. Exite                  | "<<endl;
        cout<<"\t_________________________________________"<<endl<<endl;
        cout<<" -> Type Here ...";
        cin >> value;

        if (value == 1) {
            bike++;
            system("cls");
            cout << "ENTERED BIKE" << endl;
            VEntryTime bikeEntry;
            bikeEntry.getData();
            bikeEntry.displayTime();
           // break;
        } else if (value == 2) {
            car++;
            system("cls");
            cout << "Entered a Car" << endl;
            VEntryTime carEntry;
            carEntry.getData();
            carEntry.displayTime();
            //break;
        } else if (value == 3) {
            bus++;
            system("cls");
            cout << "Entered a Bus" << endl;
            VEntryTime busEntry;
            busEntry.getData();
            busEntry.displayTime();
           // break;
        } else if (value == 4) {
            cout << "Bike: " << bike << endl;
            cout << "Car: " << car << endl;
            cout << "Bus: " << bus << endl;
        } else if (value == 5) {
            bike = 0;
            car = 0;
            bus = 0;
            system("cls");
            cout << "All Data Removed" << endl;
        } else if (value == 6) {
            exit(0);
        } else {
            cout << "Invalid choice! Please try again." << endl;
            
        }
    }

    return 0;
}


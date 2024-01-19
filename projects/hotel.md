---
layout: project
type: project
image: img/cotton/cotton-square.png
title: "Hotel Management"
date: 2023
published: true
labels:
  - C++
  - Programming
  - Team-Based
summary: "Hotel Management Based System designed by our team for our final ICS 212 project."
---

<img class="img-fluid" src="../img/cotton/cotton-header.png">

The Hotel Management Based System was a design that was created and coded by my team consisting of 5 people, for our final project in ICS 212. In class, we were tasked with creating a Hotel Library system that consisted of different actions, including managing available and unavailable hotel rooms, checking-in and checking-out customers including a receipt-based addition. My team and I worked together and utilized data structures and numerous amounts of logic and conditionals. We broke the project off into individual sections that covered various parts of the system. I was in charge of many of the different functions, including the managing of hotel rooms, and checking-in customers. Debugging was a huge step in our code as we had many errors along the way.
The Hotel Management System was a project that helped to test my abilities using C++. Before this project, we had around a couple of weeks of learning in C++, so this project tested not just my skills, but also the skills of our team. Our final allowed us to learn what it is like to collaborate with other people, with the need to utilize and develop team-based problem-solving skills.
Attached is some code from that project:
```
#include <string>
#include <iostream>

// number of available rooms in the room array (in our hotel)
int available = 0;

using namespace std;
class Customer{
    private:
        int bookingID, roomNum, advancePayment;
        long long int phoneNumber;
        string name, address;
        string bookingDates, leavingDates;   
    
    public:
        Customer() {};
        Customer (int bookingID, long long int phoneNumber, string name, string address, string bookingDates, int advancePayment){
            this->bookingID = bookingID;
            this->phoneNumber = phoneNumber;
            this->name = name;
            this->address = address;
            this->bookingDates = bookingDates;
            this->advancePayment = advancePayment;
        }
        int getBookingID() {return bookingID;}
        void setBookingID(int bookingID) {this->bookingID = bookingID;}

        string getName() {return name;}
        void setName(string name) {this->name = name;}

        string getAddress() {return address;}
        void setAddress(string address) {this->address = address;}

        long long int getPhoneNumber() {return phoneNumber;}
        void setPhoneNumber(long long int phoneNumber) {this->phoneNumber = phoneNumber;}

        string getBookingDates() {return bookingDates;}
        void setBookingDates(string bookingDates) {this->bookingDates = bookingDates;}

        string getLeavingDates() {return leavingDates;}
        void setLeavingDates(string leavingDates) {this->leavingDates = leavingDates;}

        int getAdvancePayment() {return advancePayment;}
        void setAdvancePayment(int advancePayment) {this->advancePayment = advancePayment;}

        int getRoomNum(){return roomNum;}
        void setRoomNum(int roomNum){this->roomNum = roomNum;}
};
```


# DSA

c14

#include <iostream>
#include <iomanip>
#include <queue>
using namespace std;

const int MAX_CITIES = 50;
int adj_mat[MAX_CITIES][MAX_CITIES] = {0};

void displayMatrix(int n, string cities[]) {
    cout << "\nAdjacency Matrix:" << endl;
    cout << "\t";
    for (int i = 0; i < n; i++)
        cout << setw(6) << cities[i] << "\t";
    cout << endl;
    for (int i = 0; i < n; i++) {
        cout << setw(6) << cities[i] << "\t";
        for (int j = 0; j < n; j++)
            cout << setw(6) << adj_mat[i][j] << "\t";
        cout << endl;
    }
}

void displayAdjList(int n, string cities[]) {
    cout << "\nAdjacency List:" << endl;
    for (int i = 0; i < n; i++) {
        cout << setw(6) << cities[i] << " -> ";
        for (int j = 0; j < n; j++) {
            if (adj_mat[i][j] > 0)
                cout << cities[j] << "(" << adj_mat[i][j] << ") ";
        }
        cout << endl;
    }
}

void inputCities(int &n, string cities[]) {
    cout << "Enter the number of cities: ";
    cin >> n;
    for (int i = 0; i < n; i++) {
        cout << "Enter city #" << i + 1 << " ";
        cin >> cities[i];
    }
}

void inputDistances(int n, string cities[]) {
    cout << "\nEnter distances between cities:" << endl;
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            cout << "Distance between " << cities[i] << " and " << cities[j] << " (0 for no direct connection): ";
            cin >> adj_mat[i][j];
            adj_mat[j][i] = adj_mat[i][j];
        }
    }
}

int main() {
    int n, choice;
    string cities[MAX_CITIES];
    
    cout << "\n---Menu ---\n";
    cout << "1. Enter Number of Cities & City Names\n";
    cout << "2. Enter Distances\n";
    cout << "3. Show Adjacency Matrix\n";
    cout << "4. Show Adjacency List\n";
    cout << "5. Exit\n";
    
    while (true) {
        cout << "\nEnter your choice: ";
        cin >> choice;
        
        switch (choice) {
            case 1:
                inputCities(n, cities);
                break;
            case 2:
                inputDistances(n, cities);
                break;
            case 3:
                displayMatrix(n, cities);
                break;
            case 4:
                displayAdjList(n, cities);
                break;
            case 5:
                cout << "Exiting program." << endl;
                return 0;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    }
}



output
---Menu ---
1. Enter Number of Cities & City Names
2. Enter Distances
3. Show Adjacency Matrix
4. Show Adjacency List
5. Exit

Enter your choice: 1
Enter the number of cities: 3
Enter city #1 pune
Enter city #2 mum
Enter city #3 del

Enter your choice: 2

Enter distances between cities:
Distance between pune and pune (0 for no direct connection): 0
Distance between pune and mum (0 for no direct connection): 200
Distance between pune and del (0 for no direct connection): 300
Distance between mum and mum (0 for no direct connection): 0
Distance between mum and del (0 for no direct connection): 350
Distance between del and del (0 for no direct connection): 0

Enter your choice: 3

Adjacency Matrix:
	  pune	   mum	   del	
  pune	     0	   200	   300	
   mum	   200	     0	   350	
   del	   300	   350	     0	

Enter your choice: 4

Adjacency List:
  pune -> mum(200) del(300) 
   mum -> pune(200) del(350) 
   del -> pune(300) mum(350) 

Enter your choice: 5
Exiting program.


=== Code Execution Successful ===

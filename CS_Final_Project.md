# Task 1 - 
## "Optimize the function so that it can run just O(N+M)"

```c++
#include <iostream>
#include <vector>
#include <string>
#include <unordered_set>
//Structure to hold the first & last, name, and team
struct Player {
    std::string first_name;
    std::string last_name;
    std::string team;
};
//The function to find the common players in both sports lists ( O(N+M) time )
std::vector<std::string> findCommonPlayers(
    const std::vector<Player>& basketball_players, //input list of basketball players
    const std::vector<Player>& football_players) //input list of football players
{
    std::unordered_set<std::string> seen; //hash set to store the full names of the basketball list
    for (const auto& p : basketball_players) { //goes over each basketball player
        seen.insert(p.first_name + " " + p.last_name); //adds the first last to the set
    }
    std::vector<std::string> common; // vector to hold th enames common to both sports.
    for (const auto& p : football_players) { // goes over each football player
        std::string fullname = p.first_name + " " + p.last_name; // builds the full string name
        if (seen.count(fullname)) { // checks if the name exists in the basketball set
            common.push_back(fullname);//adds it to the common list if its found
        }
    }
    return common; //returns the vector of the common names
}

int main() { // main function to check and also initialize the basketball players
    std::vector<Player> basketball_players = {
        {"Jill", "Huang", "Gators"},
        {"Janko", "Barton", "Sharks"},
        {"Wanda", "Vakulskas", "Sharks"},
        {"Jill", "Moloney", "Gators"},
        {"Luuk", "Watkins", "Gators"}
    };

    std::vector<Player> football_players = { //initializes the football player's list
        {"Hanzla", "Radosti", "32ers"},
        {"Tina", "Watkins", "Barleycorns"},
        {"Alex", "Patel", "32ers"},
        {"Jill", "Huang", "Barleycorns"},
        {"Wanda", "Vakulskas", "Barleycorns"}
    };

    auto both = findCommonPlayers(basketball_players, football_players); //checks players in both sports
    std::cout << "Players in both sports:" << "\n";
    for (const auto& name : both) {
        std::cout << "- " << name << "\n";
    }
    return 0;
}
```
# Task 2
## "Optimize the code so that the function clocks in at just O(N)."
```c++
#include <iostream>
#include <vector>
// finds the missing integer in the range 0...N
int findMissingNumber(const std::vector<int>& nums, int N) {
//The sum of 0...N is n*(n+1)/2
    long long expected_sum = (long long)N * (N + 1) / 2;
    long long actual_sum = 0; //sum of elements
    for (int x : nums) { //adds up all the numbers in the put
        actual_sum += x; //adds each element to actual_sum
    }
    return (int)(expected_sum - actual_sum);//the difference would be the missing number
}

int main() {
    // Example 1 should return 4
    std::vector<int> arr1 = {2, 3, 0, 6, 1, 5};
    std::cout << "Missing number in arr1: " << findMissingNumber(arr1, 6) << "\n";

    // Example 2 should return 1
    std::vector<int> arr2 = {8, 2, 3, 9, 4, 7, 5, 0, 6};
    std::cout << "Missing number) in arr2: " << findMissingNumber(arr2, 9) << "\n";

    return 0;
}

```
# Task 3
## "Your job is to optimize the code so that the function clocks in at just O(N)."
```c++
#include <iostream>
#include <vector>
#include <algorithm>

// returns the max profit from a buy and sell transaction
int maxProfit(const std::vector<int>& prices) {
    if (prices.empty()) return 0; //if there is nothing to trade
    int min_price = prices[0]; //the lowest price
    int best_profit = 0; //the best profit
    for (int p : prices) {//goe sthrough each day's price
        min_price = std::min(min_price, p); //updates the lowest price
        best_profit = std::max(best_profit, p - min_price); //updates the profit
    }
    return best_profit; //returns the max profit
}

int main() {
    std::vector<int> prices = {10, 7, 5, 8, 11, 2, 6}; //the sample price array
    std::cout << "Max profit: " << maxProfit(prices) << "\n"; //prints out the max profit
    return 0;
}
```
# Task 4
## "Your job is to optimize the function so that it’s a speedy O(N)."
```c++
#include <iostream>
#include <vector>
#include <climits>
#include <algorithm>

// computes the highest product of any two numbers in the array in O(N)
int highestPairProduct(const std::vector<int>& nums) {
    int max1 = INT_MIN, max2 = INT_MIN;// the largest and second largest number
    int min1 = INT_MAX, min2 = INT_MAX; //the smallest and second smallest number

    for (int x : nums) {// goes through the list
        if (x >= max1) { //checks if the current is greater than or equal to the largest
            max2 = max1; //shifts the largest to the second largest
            max1 = x; //updates the largest
        } else if (x > max2) { //else it checks if the current is greater than the second largest
            max2 = x; //updates the largest
        }
        if (x <= min1) { //if the current is less than or equal to the smallest
            min2 = min1; //shifts the smallest to the second smallest
            min1 = x; //updates the smallest
        } else if (x < min2) { //else if the current is less than the second smallest
            min2 = x; //updates the second smallest
        }
    }

    return std::max(max1 * max2, min1 * min2); //compares the product of the two largest versus the two smallest because the negatives could also give a high positive when multiplied together.
}

int main() {
    std::vector<int> nums = {5, -10, -6, 9, 4};// the sample data given
    std::cout << "Highest product of two: "
              << highestPairProduct(nums)
              << std::endl;
    return 0;
}

```

# Task 5
## Sort these values in O(N). It may be N multiplied by a constant, but that’s still considered O(N).
```c++
#include <iostream>
#include <vector>

// Sort temperature readings from 97.0 F to 99.0 F (one decimal place) in linear time
auto sortTemperatures(const std::vector<double>& readings) {
    double baseTemperature = 97.0;             // lowest possible temp
    int stepsPerDegree = 10;                   // intervals per degree - one decimal
    int distinctValues = (99 - 97) * stepsPerDegree + 1;  // total distinct readings are 21
    std::vector<int> counts(distinctValues, 0);          // the tally for each reading

    // counts each temperature
    for (double temp : readings) {
        int index = static_cast<int>((temp - baseTemperature) * stepsPerDegree + 0.5);
        counts[index]++;
    }

    // building the sorted list
    std::vector<double> sorted;
    sorted.reserve(readings.size());           // reserves the needed space
    for (int i = 0; i < distinctValues; ++i) {
        double value = baseTemperature + i / double(stepsPerDegree);
        for (int c = 0; c < counts[i]; ++c) {
            sorted.push_back(value);
        }
    }
    return sorted;                             // returns the sorted temperatures
}

int main() {
    std::vector<double> readings = {          // the given input from our assignment
        98.6, 98.0, 97.1, 99.0, 98.9,
        97.8, 98.5, 98.2, 98.0, 97.1
    };

    auto sorted = sortTemperatures(readings);  // sorts the readings
    std::cout << "Sorted readings:\n";       // displays the results
    for (double t : sorted) {
        std::cout << t << " ";
    }
    std::cout << std::endl;

    return 0;                                  
}

```
# Task 6
## "Your job is to optimize the function so that it takes O(N)time."
```c++
#include <iostream>              
#include <vector>                
#include <unordered_set>         
#include <algorithm>             // to compute the max

// to find the length of the longest  sequence in O(N) time
typedef std::vector<int> IntVector; 

int longestConsecutive(const IntVector& nums) {
   
    std::unordered_set<int> numSet(nums.begin(), nums.end()); // puts all the numbers into a set for O(1)
    int longest = 0; // variable for the longest  sequence length

    
    for (int n : nums) { //goes through each number
       
        if (!numSet.count(n - 1)) {    //starts at the beginning
            int current = n;            // variable for the current value in sequence
            int length = 1;             // variable for thecurrent sequence length

            // extends the sequence while the next consecutive number exists
            while (numSet.count(current + 1)) {
                current++;               // moves to the next number
                length++;                // increases the sequence length
            }
            // updates the longest if this sequenc was longer
            longest = std::max(longest, length);
        }
    }
    return longest; // returns the maximum sequence length found
}

int main() {
    IntVector v1 = {10, 5, 12, 3, 55, 30, 4, 11, 2}; //example 1 given should return 4
    std::cout << "Longest consecutive in v1: "
              << longestConsecutive(v1)   // calls the function on v1
              << std::endl;                // new line 

    // example 2 should return 5
    IntVector v2 = {19, 13, 15, 12, 18, 14, 17, 11};
    std::cout << "Longest consecutive in v2: "
              << longestConsecutive(v2)   // calls the function on v2
              << std::endl;                // new line

    return 0;                        
}

```

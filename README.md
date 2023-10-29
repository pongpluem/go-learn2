# go-learn2

# Link
# Go mod
https://medium.com/@uracha_p/%E0%B9%81%E0%B8%99%E0%B8%B0%E0%B8%99%E0%B8%B3%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%83%E0%B8%8A%E0%B9%89-go-module-%E0%B8%9E%E0%B8%B7%E0%B9%89%E0%B8%99%E0%B8%90%E0%B8%B2%E0%B8%99-gomod101-939242fd1e69

# Go: The Complete Developer's Guide (Golang)
  10. Go Package  ==> Execute Package (main), Reuseable Package
  11. Import Statement
      - Standard Library ==> https://pkg.go.dev/std
      - Reuseable Library
  12. File Oganization  ==> package, func, main (OP)
  14. Project Overview

  16. Variable
       - bool, string, int, float64
       - //var card string = "Hello"
       - card := "Hello"
       - fmt.Println(card)
  17. Function & Return Type
      - card := newCard()
      - func newCard() string {
	        return "Five of Diamons"
        }

  18. Slice & for loops
      - Array ==> Fix Length of list
      - Slice ==> Array that can grow
     
      - cards := []string{"Ace of Diamons", newCard()}
        cards = append(cards, "Six of spades")

      - for i, card := range cards {
          fmt.Println(i, card)
        }
        
  19. OO Appoch Vs Go Appoch
      - type deck []string

  20. Custom Type
      - type deck []string

  21. Receiver function
      - type deck []string
 	func (d deck) print() {
		for i, card := range d {		
			fmt.Println(i, card)
		}
	}

  22. create new Deck
     func newDeck() deck {
	cards := deck{}

	cardSuits := []string{"Spades", "Diamonds", "Hearts", "Clubs"}
	cardValues := []string{"Ace", "Two", "Three", "Four"}

	for _, suit := range cardSuits {
		for _, value := range cardValues {
			cards = append(cards, value+" of "+suit)
		}
	}
	return cards

     }

   23. Slice and range syntax 
       -		  0    1    2    3
       - abc := []string{"A", "B", "C", "D"}  ==> abc[0] ==> "A", abc[1] = "B"
       -  [start:number] 
       - abc[0:2]  ==> {"A", "B"}
       - abc[:2]  ==> {"A", "B"}
       - abc[2:2]  ==>
       - abc[2:]  ==>
      
       - https://go.dev/tour/moretypes/11
       - 	// Extend its length.
	s = s[:4]
	printSlice(s)
	
	a := s[:6]
	printSlice(a)

   24. Multiple return value
       - func deal(d deck, handSize int) (deck, deck) {
	return d[:handSize], d[handSize:]

       func main() {
	cards := newDeck()
	hand, remainingCards := deal(cards, 5)

	hand.print()
	remainingCards.print()
      }

   25. Byte Slice
       - ioutil
       - func WriteFile(filename string, data []byte, perm fs.FileMode) error
       - asciitable

   26. Deck to String
	- type conversion ==> []byte("Hi There!")
	- deck ==> []string ==> string ==> []byte

  27. join slice of string
      	- package strings
      	- func Join

   28. Save data to harddrive
       - func (d deck) saveToFile(filename string) error {
	return ioutil.WriteFile(filename, []byte(d.toString()), 0666)
}
       cards.saveToFile("my_cards")

    29. Reading from the harddrive
     	- func ReadFile(filename string) ([]byte, error)

        func newDeckFromFile(filename string) deck {
		bs, err := ioutil.ReadFile(filename)
		if err != nil {
			fmt.Println("Error:", err)
			os.Exit(1)
		}

		s := strings.Split(string(bs), ",")
		return deck(s)
	}

   30. Error Handling
       
   31. Shuffling a deck
       - math package
       - math/rand
       - func (d deck) shuffle() {

		for i := range d {
			newPosition := rand.Intn(len(d) - 1)

			d[i], d[newPosition] = d[newPosition], d[i]
		}
	}

 32. Random
 33. Creating a go.mod File
     - go mod init cards

 34. Testing with Go
     - go test
     - deck_test.go
     - 		package main

 36. Writing useful test
     - import (
	"testing"
	)

	func TestNewDeck(t *testing.T) {
		d := newDeck()

		if len(d) != 16 {
			t.Errorf("Expected deck length of 16, but got %v", len(d))
		}
	}

 37. Assert Elements in a skice
     - if d[0] != "Ace of Spades" {
		t.Errorf("Expected first card of Ace of Spades, but got %v", d[0])
	}

	if d[len(d)-1] != "Four of Clubs" {
		t.Errorf("Expected last card of Four of Clubs, but got %v", d[len(d)-1])
	}

 38. Testing file IO
     - func TestSaveToDeckAndNewDeckFromFile(t *testing.T) {
	os.Remove("_decktesting")

	deck := newDeck()
	deck.saveToFile("_decktesting")

	loadedDeck := newDeckFromFile("_decktesting")

	if len(loadedDeck) != 16 {
		t.Errorf("Expected 16 cards in deck, got %v", len(loadedDeck))
	}

	os.Remove("_decktesting")
	}	

   42. Struct
       - card
         - suit string  ==> Spades
         - value string ==> Ace

    43. Defining Struct

    44. Embeding Struct
    	- Struct in Struct
     	- 

    45. Struct with receiver function
    	- 

   46. Pointer
     	- package main

import "fmt"

func foo(test int) {
	test = 1 // change the value to 1
}

func bar(test *int) {
	*test = 1
}

func main() {
	var i = 0
	fmt.Println("In main, i is", i)
	foo(i)
	fmt.Println("After foo call, in main i is", i)
	bar(&i)
	fmt.Println("After bar call, in main i is", i)
}

  44. Declairing Struct
    	- type abc struct

   45. Update value of struct

   46. Embeding Struct
   47. Poiter
   48. Pass By Value
   49. Struct with Pointer
   50. Pointer Operation
   51. Pointer shortcut
   52. Gotchas With Pointer

   54. What is Map
       - Key-> Value
       - colors := Map[string]string{
       - "Red": "ff0000",
       - "Green": "00ff00",
       - "Blue": "0000ff",    <==== , must
       - }

 55. Manipulate Map
     - var colors = Map[string]string  ==> [] ==>
     - colors := make(Map[string]string)
     - colors["white"] = "#ffffff"
     - delete(colors, "white")

  56. Iterating Map
      - for key, value := range colors {
      - 
      - }

  57. Maps Vs Struct


58. Interface

59.  Problem with Inteface

60.  Interface in Practice
    - type bot interface {
	getGreeting() string
}

type englishBot struct{}
type spanishBot struct{}

func main() {
	eb := englishBot{}
	sb := spanishBot{}

	printGreeting(eb)
	printGreeting(sb)

	printGreeting2(eb)
	printGreeting2(sb)
}

func printGreeting(b bot) {
	fmt.Println(b.getGreeting())
}

func (englishBot) getGreeting() string {
	return "Hi there!"
}

63. HTTP Package
    - http.Get()

73. Custom Writer
    - type logWriter struct{}

func main() {
	resp, err := http.Get("http://google.com")
	if err != nil {
		fmt.Println("Error:", err)
		os.Exit(1)
	}

	lw := logWriter{}

	io.Copy(lw, resp.Body)
}

func (logWriter) Write(bs []byte) (int, error) {
	fmt.Println(string(bs))
	fmt.Println("Just wrote this many bytes:", len(bs))
	return len(bs), nil
}

78. Chamel and Go routine
    - Concurrent Programming

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
	       card := "Hello"
	       fmt.Println(card)
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

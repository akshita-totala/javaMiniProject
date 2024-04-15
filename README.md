package JavaMinproject.java;

import java.util.Scanner;

class Movie {
	
 	String title;
	String director;
	int duration;
	String[] actors;
	String[] roles;
	double rating;
	String genre;

	Movie(String title, String director, int duration, String[] actors, String[] roles, double rating, String genre) {
		this.title = title;
		this.director = director;
		this.duration = duration;
		this.actors = actors;
		this.roles = roles;
		this.rating = rating;
		this.genre = genre;
	}

	public void displayMovieDetails() {
		System.out.println("Movie: " + title);
		System.out.println("Directed by: " + director);
		System.out.println("Duration: " + (duration/60)+"hrs "+(duration%60) + " mins");
		System.out.print("Actors and Roles: ");
		for (int i = 0; i < actors.length; i++) {
			System.out.print(actors[i] + " as " + roles[i]);
			if (i < actors.length - 1) {
				System.out.println("\t");
			}
		}
		System.out.println();
		System.out.println("Rating: " + rating);
		System.out.println("Genre: " + genre);
	}
	}

class Theatres{

	String name;

	String [][] data = new String[4][5];



	Theatres(String name, String [][] data){

		this.name=name;

		for(int i = 0; i < 4; i++)

			this.data[i] = data[i];

	}



	void displayTheatreMDetails(int index){

		String [] dataOnThatDay = data[index];

		System.out.println("Movie Screenings on " + dataOnThatDay[0] + " in " + name + " are:");

		for(int i = 1; i < 5 ; ++i) {
			System.out.println(i + ". " + dataOnThatDay[i]);
		}

	}

}
//Akshita's Part:-

	abstract class seats{
	boolean[][] seats;
	String seatType;
	public seats(int numrows, int numcol) {
		// TODO Auto-generated constructor stub
	}
	public void seatingarr(int numrows,int numcol){
		seats = new boolean[numrows][numcol];
	}
	void displayseats(){
		System.out.println("Seating Arrangement");
		for(int i=0;i< seats.length;i++) {
			for(int j=0;j<seats[i].length;j++) {
				if(seats[i][j]) {
					System.out.println("Booked");
				}
				else {
					System.out.println("Available");
				}
			}
		}
	}
	public abstract void bookseat(int row, int col);
}

class gold extends seats{

	public gold(int numrows, int numcol) {
		super(numrows, numcol);
		seatingarr(numrows, numcol);
		seatType="Gold";
		
	}
	public void bookseat(int row, int col) {
		
		 
		 if (seats[row][col]) {
	            System.out.println("Gold seat already booked. Please select another seat.");
	        } 
		 else {
	            seats[row][col] = true;
	            System.out.println("Gold seat booked !");
	        }
		 if (row < 0 || row >= seats.length || col < 0 || col >= seats[0].length) {
	            System.out.println("Invalid row or column number. Please try again.");
	            return;
	        }
	}
}

class silver extends seats{

	 public silver(int numRows, int numCols) {
	        super(numRows, numCols);
	        seatType = "Silver";
	    }
	public void bookseat(int row, int col) {
		if (row < 0 || row >= seats.length || col < 0 || col >= seats[0].length) {
            System.out.println("Invalid row or column number. Please try again.");
            return;
        }

        if (seats[row][col]) {
            System.out.println("Silver seat already booked. Please select another seat.");
        } else {
            seats[row][col] = true;
            System.out.println("Silver seat booked!");
        }
	}
}

class bronze extends seats{
	
  	public bronze(int numRows, int numCols) {
	        super(numRows, numCols);
	        seatType = "Bronze";
	    }
	public void bookseat(int row, int col) {
		if (row < 0 || row >= seats.length || col < 0 || col >= seats[0].length) {
         System.out.println("Invalid row or column number. Please try again.");
         return;
     }

     if (seats[row][col]) {
         System.out.println("Bronze seat already booked. Please select another seat.");
     } else {
         seats[row][col] = true;
         System.out.println("Bronze seat booked!");
     }
	}
	
}


public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);
		int movieChoice=0;
		String [][][] bigData = 
			{
					{
						{"1.1.24", "Harry Potter and the Philosopher's Stone", "Dilwale Dulhania Le Jayenge", "1920 London", "Kong: Skull Island"},

						{"2.1.24", "Twilight", "Harry Potter and the Philosopher's Stone", "Kong: Skull Island", "The Matrix"},

						{"3.1.24", "The Matrix", "Joker", "Kong: Skull Island", "Bahubali: The Beginning"},

						{"4.1.24", "Tenet", "Godzilla", "Bahubali: The Beginning", "1920 London"}
					},

					{
						{"1.1.24", "Tenet", "Joker", "Bahubali: The Beginning", "The Matrix"},

						{"2.1.24", "1920 London", "Dilwale Dulhania Le Jayenge", "Bahubali: The Beginning", "The Matrix"},

						{"3.1.24", "Dilwale Dulhania Le Jayenge", "Tenet", "Harry Potter and the Philosopher's Stone", "Joker"},

						{"4.1.24", "The Matrix", "Dilwale Dulhania Le Jayenge", "Bahubali: The Beginning", "Kong: Skull Island"},

					},

					{
						{"1.1.24", "The Matrix", "Joker", "Bahubali: The Beginning", "Tenet"},

						{"2.1.24",  "Tenet", "Dune", "1920 London", "Dilwale Dulhania Le Jayenge"},

						{"3.1.24", "The Matrix", "Godzilla", "Bahubali: The Beginning", "Kong: Skull Island"},

						{"4.1.24", "Dune", "Bahubali: The Beginning", "Joker", "Tenet"},
				
					},

					{
						{"1.1.24", "The Matrix", "DDLJ", "HarryPotter", "Twilight"},

						{"2.1.24" ,"Tenet", "DDLJ", "The Matrix", "1920 London"},

						{"3.1.24", "Tenet", "Twilight", "DDLJ", "Joker"},

						{"4.1.24", "Bahubali: The Beginning", "Godzilla", "Twilight", "Kong: Skull Island"}
					}

			};

		String [] Slots = {"9:00am to 12:00pm","12:30pm to 3:30pm","4:00pm to 7:00pm","8:00pm to 11:00pm"};

		 Movie[] movies = {
            new Movie("Harry Potter and the Philosopher's Stone", "Chris Columbus", 200,
                new String[]{"Daniel Radcliffe", "Rupert Grint", "Emma Watson","Alan Rickman"," Maggie Smith"},
                new String[]{"Harry Potter", "Ron Weasley", "Hermione Granger"," Severus Snape ","Minerva McGonagall "},
                9.0, " Fantasy, Adventure"),
            new Movie("Dilwale Dulhania Le Jayenge", "Aditya Chopra", 250,
                new String[]{"Shah Rukh Khan ", "Kajol", "Amrish Puri","Farida Jalal ","Anupam Kher "},
                new String[]{"Raj Malhotra", "Simran Singh", "Chaudhry Baldev Singh"," Lajwanti Lajjo Singh","Dharamvir Malhotra "},
                9.4, " Romance, Drama"),
            new Movie("1920 London", "Tinu Suresh Desai", 224,
                new String[]{"Sharman Joshi ", "Meera Chopra", "Vishal Karwal","Sushmita Mukherjee ","Surendra Pal ","Gajendra Chauhan "},
                new String[]{"Jai Singh Gujjar", "Shivangi", "Veer Singh","Kesar Maasi"," Tantrik ","Rajasaab "},
                8.1, "Horror, Mystery"),
            new Movie("Kong: Skull Island", "Jordan Vogt-Roberts", 165,
                new String[]{"Tom Hiddleston", "Samuel L. Jackson", "Brie Larson","John C. Reilly "," John Goodman "," Corey Hawkins"},
                new String[]{"James Conrad", "Preston Packard", "Mason Weaver","Hank Marlow ", "Bill Randa ","Houston Brooks "},
                8.4, "Action, Adventure, Fantasy"),
            new Movie("Twilight", "Catherine Hardwicke", 153,
                new String[]{"Kristen Stewart", "Robert Pattinson ", "Taylor Lautner"," Peter Facinelli ","Ashley Gree ","Billy Burke "},
                new String[]{"Bella Swan", "Edward Cullen", "Jacob Black","Carlisle Cullen ","Alice Cullen "," Charlie Swan"},
                8.2, "Romance, Fantasy, Drama"),
            new Movie("The Matrix", "The Wachowskis (Lana Wachowski and Lilly Wachowski)", 183,
                new String[]{"Keanu Reeves", "Laurence Fishburne", "Carrie-Anne Moss","Hugo Weaving ","Joe Pantoliano ","Gloria Foster "},
                new String[]{"Thomas Neo Anderson", "Morpheus", "Trinity","Agent Smith ","Cypher ","The Oracle "},
                8.7, "Science Fiction, Action"),
            new Movie("Bahubali: The Beginning", "S.S. Rajamouli", 193,
                new String[]{"Prabhas ", "Rana Daggubati", "Anushka Shetty","Tamannaah ","Ramya Krishna "," Sathyaraj"},
                new String[]{"Amarendra Baahubali and Mahendra Baahubali", "Bhallaladeva", "Maharani Devasena","Avanthika ","Sivagami Devi "," Kattappa"},
                8.0, "Epic Historical Fiction, Action"),
	    new Movie("Joker", "Todd Phillips", 210,
                new String[]{"Joaquin Phoenix ", "Robert De Niro ", "Zazie Beetz","Frances Conroy ","Brett Cullen "," Shea Whigham"},
                new String[]{"Arthur Fleck / Joker", "Murray Franklin", "Sophie Dumond","Penny Fleck ","Thomas Wayne "," Detective Burke"},
               6.0, "Psychological Thriller, Drama"),
	    new Movie("Tenet", " Christopher Nolan", 180,
                new String[]{"John David Washington  ", "Robert Pattinson", "Elizabeth Debicki ","Kenneth Branagh ","Michael Caine "," Aaron Taylor-Johnson"},
                new String[]{"The Protagonist", "Neil", "Kat", "Andrei Sator ","Sir Michael Crosby ","  Ives"},
                7.0, "Action, Sci-Fi, Thriller"),
	    new Movie("Godzilla", "Gareth Edwards", 120,
                new String[]{"Aaron Taylor-Johnson ", "Bryan Cranston", "Ken Watanabe","Elizabeth Olsen","Sally Hawkins  "},
                new String[]{"Ford Brody", "Joe Brody", "Dr. Ishiro Serizawa"," Elle Brody "," Dr. Vivienne Graham "},
                7.3, "Action, Science Fiction"),
	    new Movie("Dune", "Denis Villeneuve", 190,
                new String[]{"Timothée Chalamet ", "Rebecca Ferguson", "Oscar Isaac","Josh Brolin","Stellan Skarsgård","Dave Bautista ","Zendaya"},
                new String[]{" Paul Atreides", "Lady Jessica", "Duke Leto Atreides"," Gurney Halleck "," Baron Vladimir Harkonnen "," Glossu Rabban ","Chani "},
                9.4, " Science Fiction, Adventure"),
		
        };

		Theatres  theatres [] = new Theatres[4];
		
		String theatreNames [] = {"INOX", "Mukta Theatres", "City Pride", "AURUM"};
  
		String movieNames [] = {"Harry Potter and the Philosopher's Stone","Dilwale Dulhania Le Jayenge","1920 London",
  	"Kong: Skull Island","Twilight","The Matrix","Bahubali: The Beginning","Joker","Tenet","Godzilla","Dune"};
		for(int i = 0; i < 4; ++i) {
			theatres[i] = new Theatres(theatreNames[i],bigData[i]);
		}
	  int numrows = 8; 
	    int numcols = 10;
     //obj[theatre][date][movie][slot]
		gold goldSeating[][][][]=new gold[4][4][11][4];
		silver silverSeating[][][][]=new silver[4][4][11][4];
		bronze bronzeSeating[][][][]=new bronze[4][4][11][4];
		for(int a=0;a<4;a++) {
			for(int b=0;b<4;b++) {
				for(int c=0;c<11;c++) {
					for(int d=0;d<4;d++) {
						goldSeating[a][b][c][d]=new gold(numrows, numcols);
						silverSeating[a][b][c][d]=new silver(numrows, numcols);
						bronzeSeating[a][b][c][d]=new bronze(numrows, numcols);
					}
				}
			}
		}
	  int rerunChoice=1;
//RUN CODE FROM HERE ON
		
  	do{
		System.out.println("Theatres at your service:");

		for(int i = 0; i < 4; ++i) System.out.println((i + 1) + ": " + theatreNames[i]);

		System.out.print("Choose the Theatre you want to book at: ");

		int theatreChoice = sc.nextInt();



		System.out.println("\nAvailable dates for booking:");

		System.out.println("1) 1.1.24\n2) 2.1.24\n3) 3.1.24\n4) 4.1.24");

		System.out.print("Choose a suitable date: ");

		int dateChoice = sc.nextInt();



	//System.out.println("\nMovie Screenings on "+bigData[theatreChoice-1][dateChoice-1][0]+" at "+theatreNames[theatreChoice-1]+":");

		theatres[theatreChoice - 1].displayTheatreMDetails(dateChoice - 1);
		sc.nextLine();
		boolean flag=false;
		do {
			System.out.println("\nWhat are you Watching then?");
			System.out.print("Type in your Choice: ");

			String movieChoiceS = sc.nextLine();

			for(int k=0;k<11;k++){
				if(movieNames[k].equals(movieChoiceS)){
					movieChoice=k+1;
					flag=true;
					break;
				}
			}
			if(!flag) {
				System.out.println("Incorrect Movie Name entered! Try Again!");
			}
		}while(!flag);
		System.out.println("\nEnter '1' to view Movie Details.\nElse, Enter 0.");

		System.out.print("Your Choice: ");
		int tempChoice=sc.nextInt();

		//The following code will be executed on demand for movie details.. create an obj of the movie details class 

		//and call it with the given parameter

		if(tempChoice==1) {
			movies[movieChoice-1].displayMovieDetails();
		}

		System.out.println("\nSlots Available are:");

		for(int i = 0; i < 4; i++) System.out.println((i + 1) + ": " + Slots[i]);

		System.out.print("Choose a Slot: ");

		int slotChoice = sc.nextInt();

		//Here comes the code for seats followed by (continued booking / final billing)
		//Here comes the code for continued booking i.e.,  final billing
 	//Akshita's Part:-
 	//Scanner scanner = new Scanner(System.in);
		 int ch;
		 /*gold goldSeating = new gold(numrows, numcols);
		 silver silverSeating = new silver(numrows, numcols);
		 bronze BronzeSeating = new bronze(numrows, numcols);*/
		 System.out.print("Enter Number of seats you want to book: ");
		 int no=sc.nextInt();
		 for(int i=0;i<no;i++) {
			 
		 
	     System.out.println("Which Zone would you like to book a seat in");
	     System.out.println("1.Gold( Rows 1-2, Col:1-10)\n2.Silver(Rows 3-5, Col:1-10)\n3.Bronze(Rows 6-8, Col:1-10)\n");
	     ch=sc.nextInt();
	     System.out.println("Give row and column:");
	     int n=sc.nextInt();
	     int c=sc.nextInt();
	     
	     
	     switch(ch) {
	     case 1:
	    	 
		     
		     System.out.println("Give row and column:");
		     

		     goldSeating[theatreChoice-1][dateChoice-1][movieChoice-1][slotChoice-1].bookseat(n,c);
		     //goldSeating[theatreChoice-1][dateChoice-1][movieChoice-1][slotChoice-1].displayseats();
		     break;
	     
		case 2:
			
		     
		     System.out.println("Give row and column:");
		     
		     silverSeating[theatreChoice-1][dateChoice-1][movieChoice-1][slotChoice-1].bookseat(n,c);
		     silverSeating[theatreChoice-1][dateChoice-1][movieChoice-1][slotChoice-1].displayseats();
		     break;
	    
	     case 3:
	    	
		     
		     bronzeSeating[theatreChoice-1][dateChoice-1][movieChoice-1][slotChoice-1].bookseat(numrows,numcols);
		     bronzeSeating[theatreChoice-1][dateChoice-1][movieChoice-1][slotChoice-1].displayseats();
		     break;
	     default:
	    	 System.out.println("Invalid choice");
	    	 break;
	     } 
		 }
  
 	System.out.println("Enter '1' to further continue booking. \nElse, enter 0 to generate Bill.");
  	 rerunChoice=sc.nextInt();
	    }while(rerunChoice==1);
	       
	   //Here comes the code for continued booking i.e.,  final billing
    //VARDA'S PART:

	}

	}

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Billing {
    // Define prices for theaters, movies, and seat types
    private static final List<String> theaters = Arrays.asList("INOX", "Mukta Theatres", "City Pride", "AURUM");
    private static final List<String> movies = Arrays.asList("Harry Potter and the Philosopher's Stone",
                                                              "Dilwale Dulhania Le Jayenge",
                                                              "1920 London",
                                                              "Kong: Skull Island",
                                                              "Twilight",
                                                              "The Matrix",
                                                              "Bahubali: The Beginning",
                                                              "Joker",
                                                              "Tenet",
                                                              "Godzilla",
                                                              "Dune");
    private static final List<String> seatTypes = Arrays.asList("Gold", "Silver", "Bronze");
    private static final double[][] theaterPrices = {
            {60.0, 70.0, 65.0, 80.0},  // Prices for INOX
            {65.0, 75.0, 70.0, 85.0},  // Prices for Mukta Theatres
            {70.0, 80.0, 75.0, 90.0},  // Prices for City Pride
            {75.0, 85.0, 80.0, 95.0}   // Prices for AURUM
    };
    private static final double[] moviePrices = {50.0, 60.0, 55.0, 65.0, 55.0, 65.0, 60.0, 55.0, 70.0, 65.0, 70.0};
    private static final double[] seatPrices = {100.0, 80.0, 60.0};

    public static double calculateTotalCost(int theaterIndex, int movieIndex, int seatIndex, int numSeats) {
        double theaterPrice = theaterPrices[theaterIndex][seatIndex];
        double moviePrice = moviePrices[movieIndex];
        double seatPrice = seatPrices[seatIndex];

        // Calculate subtotal
        double subtotal = (theaterPrice + moviePrice + seatPrice) * numSeats;
        double tax = subtotal * 0.19; // Assuming 19% GST
        double totalCost = subtotal + tax;

        // Print the bill
        printBill(theaterIndex, movieIndex, seatIndex, numSeats, theaterPrice, moviePrice, seatPrice, subtotal, tax, totalCost);

        return totalCost; // Return total cost including tax
    }

    // Method to print the bill
    private static void printBill(int theaterIndex, int movieIndex, int seatIndex, int numSeats,
                                   double theaterPrice, double moviePrice, double seatPrice,
                                   double subtotal, double tax, double totalCost) {
        String theaterName = theaters.get(theaterIndex);
        String movieName = movies.get(movieIndex);
        String seatType = seatTypes.get(seatIndex);

        System.out.println("\n*");
        System.out.println("************ MOVIE BILL ***********");
        System.out.println("*\n");
        System.out.println("Theater: " + theaterName);
        System.out.println("Movie: " + movieName);
        System.out.println("Seat Type: " + seatType);
        System.out.println("Number of Seats: " + numSeats);
        System.out.println("-----------------------------------");
        System.out.println("Theater Price: ₹" + theaterPrice);
        System.out.println("Movie Price: ₹" + moviePrice);
        System.out.println("Seat Price: ₹" + seatPrice);
        System.out.println("-----------------------------------");
        System.out.println("Subtotal: ₹" + subtotal);
        System.out.println("Tax (GST 19%): ₹" + tax);
        System.out.println("Total Cost: ₹" + totalCost);
        System.out.println("\n*\n");
    }
}

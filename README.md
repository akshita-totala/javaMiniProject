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

	String [] data = new String[4];



	Theatres(String name, String [] data){

		this.name=name;

		for(int i = 0; i < 4; i++)

			this.data[i] = data[i];

	}



	void displayTheatreMDetails(int index){

		String [] dataOnThatDay = data[index].split(" ");

		System.out.println("The Movies Available on " + dataOnThatDay[0] + " in " + name + " are:");

		for(int i = 1; i < 5 ; ++i) System.out.println(i + ". " + dataOnThatDay[i]);

	}

}



public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		String [][] bigData = {{"1.1.24 HarryPotter DDLJ 1920London Kong",

			"2.1.24 Twilight HarryPotter Kong Matrix",

			"3.1.24 Bahubali Joker Kong Bahubali",

			"4.1.24 Tenet Godzilla Bahubali 1920London",

		},

		{"1.1.24 Tenet Joker Bahubali Matrix",

			"2.1.24 1920London DDLJ Bahubali Matrix",

			"3.1.24 DDLJ Tenet HarryPotter Joker",

			"4.1.24 Matrix DDLJ Bahubali DDLJ",

		},

		{"1.1.24 Matrix Joker Matrix Tenet",

			"2.1.24  Tenet 19Dune20London Tenet",

			"3.1.24 Matrix Godzilla Bahubali Kong",

			"4.1.24 Dune Bahubali Joker Tenet",

		},

		{"1.1.24 Matrix DDLJ HarryPotter Twilight",

			"2.1.24 Tenet DDLJ Matrix 1920London",

			"3.1.24 Tenet Twilight DDLJ Joker",

			"4.1.24 Bahubali Godzilla Twilight Kong",

		}};

	    String [] Slots = {"9:00am to 12:00pm","12:30pm to 3:30pm","4:00pm to 7:00pm","8:00pm to 11:00pm"};
     
//AADITI YOU HAVE TO INSERT DATA HERE!!..in pace of these already existing movies.. insert the new movies ka details!!

		 Movie[] movies = {
            new Movie("3 Idiots", "Rajkumar Hirani", 170,
                new String[]{"Aamir Khan", "Kareena Kapoor", "R. Madhavan"},
                new String[]{"Rancho", "Pia", "Farhan"},
                8.4, "Comedy, Drama"),
            new Movie("Dangal", "Nitesh Tiwari", 161,
                new String[]{"Aamir Khan", "Fatima Sana Shaikh", "Sanya Malhotra"},
                new String[]{"Mahavir Singh Phogat", "Geeta Phogat", "Babita Kumari"},
                8.4, "Biography, Drama, Sport"),
            new Movie("Lagaan", "Ashutosh Gowariker", 224,
                new String[]{"Aamir Khan", "Gracy Singh", "Rachel Shelley"},
                new String[]{"Bhuvan", "Gauri", "Elizabeth Russell"},
                8.1, "Adventure, Drama, Musical"),
            new Movie("Taare Zameen Par", "Aamir Khan", 165,
                new String[]{"Darsheel Safary", "Aamir Khan", "Tisca Chopra"},
                new String[]{"Ishaan Awasthi", "Ram Shankar Nikumbh", "Maya Awasthi"},
                8.4, "Drama, Family, Music"),
            new Movie("PK", "Rajkumar Hirani", 153,
                new String[]{"Aamir Khan", "Anushka Sharma", "Sushant Singh Rajput"},
                new String[]{"PK", "Jaggu", "Sarfaraz"},
                8.1, "Comedy, Drama, Fantasy"),
            new Movie("Dil Chahta Hai", "Farhan Akhtar", 183,
                new String[]{"Aamir Khan", "Saif Ali Khan", "Akshaye Khanna"},
                new String[]{"Akash", "Sameer", "Siddharth"},
                8.1, "Comedy, Drama, Romance"),
            new Movie("Kabhi Alvida Naa Kehna", "Karan Johar", 193,
                new String[]{"Shah Rukh Khan", "Rani Mukerji", "Abhishek Bachchan"},
                new String[]{"Dev Saran", "Maya Talwar", "Rishi Talwar"},
                6.1, "Drama, Romance"),
        };


		Theatres  theatres [] = new Theatres[4];

		String theatreNames [] = {"INOX", "Mukta Theatres", "City Pride", "AURUM"};

		for(int i = 0; i < 4; ++i) {
			theatres[i] = new Theatres(theatreNames[i],bigData[i]);
		}

		System.out.println("Theatres at your service:");

		for(int i = 0; i < 4; ++i) System.out.println((i + 1) + ": " + theatreNames[i]);

		System.out.print("Choose the Theatre you want to book at: ");

		int theatreChoice = sc.nextInt();



		System.out.println("Available dates for booking:");

		System.out.println("1) 1.1.24\n2) 2.1.24\n3) 3.1.24\n4) 4.1.24");

		System.out.println("Choose a suitable date: ");

		int dateChoice = sc.nextInt();



		System.out.println("Movie Screenings on the chosen day:");

		theatres[theatreChoice - 1].displayTheatreMDetails(dateChoice - 1);

		System.out.print("What are you Watching then?");

		sc.nextLine();

		String movieChoice = sc.nextLine();

		

		System.out.println("Enter: \n1. Movie Details\n2. Proceed with Booking");

		int tempChoice=sc.nextInt();

		//The following code will be executed on demand for movie details.. create an obj of the movie details class 

		//and call it with the given parameter

		if(tempChoice==1) {
  
        //AADITI KA PART
        
		//	movieobj.displayMovieDettais(movieChoice);

		}

		System.out.println("Slots Available are:");

		for(int i = 0; i < 4; ++i) System.out.println((i + 1) + ": " + Slots[i]);

		System.out.print("Choose a Slot: ");

		int slotChoice = sc.nextInt();

			//Here comes the code for seats followed by (continued booking / final billing)

    }
}

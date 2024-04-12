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

		System.out.println("The Movies Available on " + dataOnThatDay[0] + " in " + name + " are:");

		for(int i = 1; i < 5 ; ++i) {
			System.out.println(i + ". " + dataOnThatDay[i]);
		}

	}

}



public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);

		String [][][] bigData = 
			{
					{
						{"1.1.24", "HarryPotter", "DDLJ", "1920London", "Kong"},

						{"2.1.24", "Twilight", "HarryPotter", "Kong", "Matrix"},

						{"3.1.24 Bahubali Joker Kong Bahubali"},

						{"4.1.24 Tenet Godzilla Bahubali 1920London"}
					},

					{
						{"1.1.24 Tenet Joker Bahubali Matrix"},

						{"2.1.24 1920London DDLJ Bahubali Matrix"},

						{"3.1.24 DDLJ Tenet HarryPotter Joker"},

						{"4.1.24 Matrix DDLJ Bahubali DDLJ"},

					},

					{
						{"1.1.24 Matrix Joker Matrix Tenet"},

						{"2.1.24  Tenet Dune 1920London Tenet"},

						{"3.1.24 Matrix Godzilla Bahubali Kong"},

						{"4.1.24 Dune Bahubali Joker Tenet"},
				
					},

					{
						{"1.1.24 Matrix DDLJ HarryPotter Twilight"},

						{"2.1.24 Tenet DDLJ Matrix 1920London"},

						{"3.1.24 Tenet Twilight DDLJ Joker"},

						{"4.1.24 Bahubali Godzilla Twilight Kong"}
					}

			};

		String [] Slots = {"9:00am to 12:00pm","12:30pm to 3:30pm","4:00pm to 7:00pm","8:00pm to 11:00pm"};

		//AADITI YOU HAVE TO INSERT DATA HERE!!..in pace of these already existing movies.. insert the new movies ka details!!

		 Movie[] movies = {
            new Movie("Harry Potter and the Philosopher's Stone", "Chris Columbus", 200,
                new String[]{"Daniel Radcliffe", "Rupert Grint", "Emma Watson","Alan Rickman"," Maggie Smith"},
                new String[]{"Harry Potter", "Ron Weasley", "Hermione Granger"," Severus Snape ","Minerva McGonagall "},
                9.0, " Fantasy, Adventure"),
            new Movie("Dilwale Dulhania Le Jayenge ", "Aditya Chopra", 250,
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
            new Movie("Baahubali: The Beginning", "S.S. Rajamouli", 193,
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

		for(int i = 0; i < 4; ++i) {
			theatres[i] = new Theatres(theatreNames[i],bigData[i]);
		}

		System.out.println("Theatres at your service:");

		for(int i = 0; i < 4; ++i) System.out.println((i + 1) + ": " + theatreNames[i]);

		System.out.print("Choose the Theatre you want to book at: ");

		int theatreChoice = sc.nextInt();



		System.out.println("\nAvailable dates for booking:");

		System.out.println("1) 1.1.24\n2) 2.1.24\n3) 3.1.24\n4) 4.1.24");

		System.out.print("Choose a suitable date: ");

		int dateChoice = sc.nextInt();



		System.out.println("\nMovie Screenings on "+bigData[theatreChoice-1][dateChoice-1][0]+"at"+theatreNames[theatreChoice-1]+":");

		theatres[theatreChoice - 1].displayTheatreMDetails(dateChoice - 1);

		System.out.print("What are you Watching then?\n Enter your Choice: ");

		sc.nextLine();

		String movieChoice = sc.nextLine();



		System.out.println("\nEnter '1' to view Movie Details.\nElse, Enter 0.");

		System.out.print("Enter your Choice: ");
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
		//Here comes the code for continued booking i.e.,  final billing

	}
}

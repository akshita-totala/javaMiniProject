# javaMiniProject
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
        System.out.println("Duration: " + duration + " mins");
        System.out.print("Actors and Roles: ");
        for (int i = 0; i < actors.length; i++) {
            System.out.print(actors[i] + " as " + roles[i]);
            if (i < actors.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println();
        System.out.println("Rating: " + rating);
        System.out.println("Genre: " + genre);
    }
}

class Theater {
    String name;
    String location;

    Theater(String name, String location) {
        this.name = name;
        this.location = location;
    }

    void displayMovieDetails(Movie movie) {
        System.out.println("Movie details for " + movie.title + " at " + this.name + ", " + this.location + ":");
        movie.displayMovieDetails();
    }
}

public class MovieBookingSystem {
    public static void main(String[] args) {
        Theater[] theaters = {
            new Theater("Theater-1", "Karvenagar"),
            new Theater("Theater-2", "Chandini Chowk"),
            new Theater("Theater-3", "Pavelion Mall"),
            new Theater("Theater-4", "Amanora Mall"),
            new Theater("Theater-5", "JVA Mall"),
            new Theater("Theater-6", "Shivajinagar"),
            new Theater("Theater-7", "Phoenix")
        };

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

 
        Scanner scanner = new Scanner(System.in);
        int choice;
        do {
            System.out.println("1. Display movie details");
            System.out.println("0. Exit");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    displayMovieDetails(scanner, theaters, movies);
                    break;
                case 0:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 0);
    }

    public static void displayMovieDetails(Scanner scanner, Theater[] theaters, Movie[] movies) {
        System.out.println("Select a theater:");
        for (int i = 0; i < theaters.length; i++) {
            System.out.println((i + 1) + ". " + theaters[i].name);
        }
        System.out.print("Enter theater choice: ");
        int theaterChoice = scanner.nextInt();
        if (theaterChoice >= 1 && theaterChoice <= theaters.length) {
            System.out.println("Select a movie:");
            for (int i = 0; i < movies.length; i++) {
                System.out.println((i + 1) + ". " + movies[i].title);
            }
            System.out.print("Enter movie choice: ");
            int movieChoice = scanner.nextInt();
            if (movieChoice >= 1 && movieChoice <= movies.length) {
                theaters[theaterChoice - 1].displayMovieDetails(movies[movieChoice - 1]);
            } else {
                System.out.println("Invalid movie choice.");
            }
        } else {
            System.out.println("Invalid theater choice.");
        }
    }
}

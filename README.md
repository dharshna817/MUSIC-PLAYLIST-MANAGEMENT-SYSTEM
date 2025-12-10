#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Song {
    char title[100];
    char artist[100];
    float duration;
    struct Song* next;
};

struct Song* head = NULL;

struct Song* createSong(char title[], char artist[], float duration) {
    struct Song* newSong = (struct Song*)malloc(sizeof(struct Song));
    strcpy(newSong->title, title);
    strcpy(newSong->artist, artist);
    newSong->duration = duration;
    newSong->next = NULL;
    return newSong;
}

void addSong(char title[], char artist[], float duration) {
    struct Song* song = createSong(title, artist, duration);
    if (head == NULL) {
        head = song;
    } else {
        struct Song* temp = head;
        while (temp->next != NULL)
            temp = temp->next;
        temp->next = song;
    }
    printf("🎵 Song added: %s\n", title);
}

void displayPlaylist() {
    if (head == NULL) {
        printf("Playlist is empty.\n");
        return;
    }
    struct Song* temp = head;
    int i = 1;
    printf("\n🎧 Playlist:\n");
    while (temp != NULL) {
        printf("%d. %s by %s [%.2f min]\n", i++, temp->title, temp->artist, temp->duration);
        temp = temp->next;
    }
}

void deleteSong(char title[]) {
    struct Song *temp = head, *prev = NULL;
    while (temp != NULL && strcmp(temp->title, title) != 0) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) {
        printf("❌ Song not found: %s\n", title);
        return;
    }
    if (prev == NULL) {
        head = temp->next;
    } else {
        prev->next = temp->next;
    }
    free(temp);
    printf("🗑 Song deleted: %s\n", title);
}

void playNext() {
    if (head == NULL) {
        printf("No songs to play.\n");
        return;
    }
    printf("▶ Now playing: %s by %s\n", head->title, head->artist);
    struct Song* temp = head;
    head = head->next;
    free(temp);
}

void countSongs() {
    int count = 0;
    struct Song* temp = head;
    while (temp != NULL) {
        count++;
        temp = temp->next;
    }
    printf("📊 Total songs: %d\n", count);
}

void menu() {
    printf("\n--- Music Playlist Menu ---\n");
    printf("1. Add Song\n");
    printf("2. Display Playlist\n");
    printf("3. Delete Song\n");
    printf("4. Play Next Song\n");
    printf("5. Count Songs\n");
    printf("6. Exit\n");
}

void addTamilSongs() {
    addSong("Anbil Avan", "A.R. Rahman", 4.20);
    addSong("Munbe Vaa", "Shreya Ghoshal", 4.50);
    addSong("Aalaporaan Thamizhan", "A.R. Rahman", 5.00);
    addSong("Vaathi Coming", "Anirudh Ravichander", 3.45);
    addSong("Why This Kolaveri Di", "Dhanush", 4.05);
    addSong("Selfie Pulla", "Vijay", 4.10);
    addSong("Surviva", "Anirudh", 3.55);
    addSong("Rowdy Baby", "Dhanush", 3.40);
    addSong("Thaarame Thaarame", "Sid Sriram", 4.25);
    addSong("Chinna Chinna Aasai", "Minmini", 4.15);
    addSong("Kanave Kanave", "Anirudh", 4.10);
    addSong("Enna Solla Pogirai", "Shweta Mohan", 4.45);
    addSong("Kadhal Rojave", "S.P. Balasubrahmanyam", 4.30);
    addSong("Kanne Kalaimaane", "S.P. Balasubrahmanyam", 3.50);
    addSong("Naan Pizhaippeno", "Sid Sriram", 4.35);
    addSong("Oru Deivam Thantha Poove", "Karthik", 4.20);
    addSong("Unakkenna Venum Sollu", "Harris Jayaraj", 4.00);
    addSong("Suttrum Vizhi", "Harris Jayaraj", 3.55);
    addSong("Neeyum Naanum", "Yuvan Shankar Raja", 4.45);
    addSong("Pookkal Pookkum", "Roja", 4.30);
    addSong("Yethi Yethi", "Anirudh", 3.30);
    addSong("Vinnaithaandi Varuvaayaa", "Karthik", 5.10);
    addSong("Ennodu Nee Irundhaal", "Sid Sriram", 4.25);
    addSong("Aagayam Theepidicha", "Sid Sriram", 4.05);
    addSong("Maruvaarthai", "Sid Sriram", 4.20);
    addSong("High On Love", "Sid Sriram", 3.45);
    addSong("Veyyon Silli", "G.V. Prakash", 4.00);
    addSong("Petta Theme", "Anirudh", 3.10);
    addSong("Bujji", "Anirudh", 3.35);
    addSong("Kutti Story", "Thalapathy Vijay", 4.10);
    addSong("Vaathi Raid", "Anirudh", 3.25);
    addSong("Sandakari Neethan", "Vijay Yesudas", 4.00);
    addSong("Dippam Dappam", "Anirudh", 3.50);
    addSong("Tum Tum", "Sri Vardhini", 4.05);
    addSong("Neethane", "Yuvan Shankar Raja", 4.40);
    addSong("Kadhal Sadugudu", "S.P.B", 4.25);
    addSong("Uyire Uyire", "Hariharan", 4.55);
    addSong("Kannazhaga", "Dhanush", 3.55);
    addSong("Oh Penne", "Anirudh", 4.00);
    addSong("Mental Manadhil", "A.R. Rahman", 3.35);
    addSong("Pachai Nirame", "Hariharan", 5.00);
    addSong("Thee Thee", "Shankar Mahadevan", 4.10);
    addSong("Oru Kal Oru Kannadi", "Yuvan", 3.45);
    addSong("Sutthi Sutthi", "Santhosh Narayanan", 3.30);
    addSong("Mellisaye", "Pradeep Kumar", 4.00);
    addSong("Nenjukkul Peidhidum", "Harris Jayaraj", 4.20);
    addSong("Kangal Irandal", "Vijay Yesudas", 3.55);
    addSong("Kadhale Kadhale", "Sid Sriram", 4.35);
    addSong("Nee Partha Vizhigal", "Chinmayi", 4.15);
    printf("✅ 50 Tamil songs added to the playlist!\n");
}

int main() {
    int choice;
    char title[100], artist[100];
    float duration;

    addTamilSongs();

    while (1) {
        menu();
        printf("Enter choice: ");
        scanf("%d", &choice);
        getchar();

        switch (choice) {
            case 1:
                printf("Enter song title: ");
                fgets(title, sizeof(title), stdin);
                title[strcspn(title, "\n")] = 0;
                printf("Enter artist: ");
                fgets(artist, sizeof(artist), stdin);
                artist[strcspn(artist, "\n")] = 0;
                printf("Enter duration (in minutes): ");
                scanf("%f", &duration);
                addSong(title, artist, duration);
                break;
            case 2:
                displayPlaylist();
                break;
            case 3:
                printf("Enter song title to delete: ");
                fgets(title, sizeof(title), stdin);
                title[strcspn(title, "\n")] = 0;
                deleteSong(title);
                break;
            case 4:
                playNext();
                break;
            case 5:
                countSongs();
                break;
            case 6:
                printf("Exiting Music Playlist System.\n");
                exit(0);
            default:
                printf("Invalid choice. Try again.\n");
        }
    }
    return 0;
}

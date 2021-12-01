# Tune Tip Requirements

## Common Acroynyms Used Through Documentation

- **UI:** User interface
- **ML:** Machine learning
- **AI:** Artifical intellegence
- **CORS:** Cross Origin Resource Sharing

## Introduction

The purpose of the requirements documentation is to provide the reader with understanding of the layout of our solution Tune Tip. We are currently storing all our documentation in GitHub and will refer to any detailed documentation needed to our Capstone-Documentation repository within our organization we set up. The detailed scope of this product can be found at this [link](https://github.com/Group6CapstoneGroup/Capstone-Documents/tree/main/Project%20Plan%20and%20Umbrella%20Activities/Scope%20Statement%20Assignment). You can also find a list of the tools we utilized to build/develop our product here at this [link](https://github.com/Group6CapstoneGroup/Capstone-Documents/tree/main/Project%20Plan%20and%20Umbrella%20Activities/Tools%20%26%20Standards). We are currently using utilizing Markdown to write up most of our documentation. The reason being is it’s simple, proficent at formatting, and makes referencing other documentation in our organization easy.

## General Description

The general description and idea of Tune Tip came about from solving a common problem Paige and I had. We both live a somewhat active lifestyle and wanted to build a music recommendation application that was specific to the listener's own interests. We already were aware that other streaming platforms like Apple Music, Prime Music, Spotify provide a music recommendation service. What makes Tune Tip unique is the possibilities and customization of it. The idea would be to have Tune Tip be able to integrate with all major streaming platforms. This way our dataset and findings won't just be from customers of one music streaming platform like our competitors. For example, Apple only receives feedback and findings on their recommendations based on their Apple Music users. We would have users from a variety of streaming platforms. This would allow us to build more complex recommendation models. We could also customize the recommendation models based on what attribute we wanted the model to make a prediction model. For instance, if I wanted to listen to songs at a specific tempo, I could instruct the model to find other songs that are like songs on my playlist that have a specific tempo I am wanting. For the sake and time/resources of this project we are currently utilizing a recommendation finder to recommend songs based on song title and artist only. The possibilities for a solution like Tune Tip are endless.

With ML/AI advancing in the technical world we could provide our potential customers with customized recommendations and partner with some of the leading music streaming providers. The goal for Tune Tip is to be as automated as possible from end to end. Meaning we can automate extracting the data from the streaming platform to get the user's playlists. We are then able to make song recommendations based on what the user is looking for, again for the sake of this project we are utilizing song title and artist. Once the user is satisfied and has found songs to freshen up their playlist, we can then sync the data and add the new tracks to the user's streaming account with no manual entry on the user's part. For the sake of this product, we have already manually input a list of dummy music data to play with to show how the product works.

## Specific Requirements

### UI

- **1.0.0:** Create a user friendly homepage that is easy to navigate and explains what the application is set to do.
  - **1.0.1:** The homepage will display a navigation bar with the app name toggled to the left and three clickable links toggled to the right.
  - **1.0.2:** The first link will be labeled Home. If clicked the user will be redirected to the homepage of the application.
  - **1.0.3:** The second link will be labeled About. If clicked the user will be redirected to the about section of the application. This form displays the about content of Tune Tip.
  - **1.0.4:** The third link will be labeled Support. If clicked the user will be redirected to the support section of the application. This form displays user instructions and a support contact.

- **1.1.0:** Because we offer a platform that ideally integrates will multiple streaming services, provide a way to log into the program and selecting the streaming platform the user currently utilizes.

- **1.2.0:** Provide a way to secure details until user is successfully logged into application. Data should not be visible to just anyone who logs into the application.
  - **1.2.1** For this application and playing with dummy data we will set dummy login credentials that are needed to go utilize application features.

- **1.3.0:** Once user has successfully been authenticated please navigate to the account page so the user can see their music data extracted.

- **1.4.0:** Populate a selectable data grid with music information, this way the user can individually check each row item they would like to feed to the recommendation model.

- **1.5.0:** On the account screen add a button to feed selected music to recommendation model.
  - **1.5.1:** If pressed the UI should navigate to the recommendation page of the UI.

- **1.6.0:** On the account screen add a sync button to sync music data to the user's streaming account.
  - **1.6.1:** If pressed the UI should display a loader screen to the user to indicate the syncing is happening and the user should not be able to access any other functionality until syncing is done.
  
- **1.7.0:** The recommendation screen will display the music data the user has selected to feed to the recommendation model.
  - **1.7.1:** The data will be displayed in a non-selectable data grid.

- **1.8.0:** Below the data grid there will be 3 buttons.
  - **1.8.1:** The first button will be labeled add songs. If clicked the user redirected to the account page, this is where they can add more songs to feed to recommendation model.
  - **1.8.2:** The second is a button labeled delete list. If the clicked the music selection list will be cleared out. The user will then be redirected to the account page where they can select a new list of music to send to recommendation model.
  - **1.8.3:** The third is a button submit. If the clicked the UI will populate a spinner to indicate to the user the song data is being fed to the recommendation model. Once completed and we get recommendations back the loading indicator will stop and recommendations will be displayed.

- **1.9.0:** The recommendations we received from the recommendation model will be displayed in a selectable data grid.
  - **1.9.1:** This data grid will include the columns: artist, track, playlist.

- **2.0.0:** The user has the ability to select the specified rows they would like to add to their music playlist.
- **2.1.0:** Under the data grid with the listed recommendations there will be a button labeled Add Songs.
  - **2.1.1:** If clicked the user will be redirected back to the account page where they will see their newly updated playlist.

### Music Service

- **1.0.0:** Music-service will have two separate models it will work with the first being music model and the second being selected song model.
  - **1.0.1:** Both these models have the same attributes: recordId, recordNumber, track, artist, playlist, album.
  - **1.0.2:** music model will be the original data from the user that we save and keep as a reference when extracting and importing data to streaming the user's streaming service. This information will be stored in it's own table in the database.
  - **1.0.3:** selected song model will be the data the user interacts with our recommendation model with. This information will be stored in its own table in the database.
- **1.1.0:** Music service will contain a controller for music model. This controller is what the UI will ping when it makes request for information from music service (CORS).
  - **1.1.1:** The controller will contain a number of requests for GET, POST and DELETE functionality.
  - **1.1.2:** The first method in music controller will be GetMusic(). This method will return a list of music it gets back from music service.
  - **1.1.3:** The second method in music controller will be GetTrack(). This method will return a single music item with the corresponding record number the user entered in.
  - **1.1.4:** The third method in music controller will be CreateMusicRecordAsync(). This method will create a new music model entry in the database with the fields: track, artist, album, and playlist specified by the user in the request.
  - **1.1.5:** The fourth method in music controller will be DeleteTrack(). This method will delete the music object that corresponds to the record number entered in by the user.
- **1.2.0:** Music service will contain a controller for selected song model. This controller is what the UI will ping when it makes request for information from music service.
  - **1.2.1:** This controller will contain a number of requests for GET, POST and Delete functionality
  - **1.2.2:** The first method in selected song controller will be GetSelectedSongs(). This method will make a call to the selected song service and return a list of the selected songs it currently has in the database.
  - **1.2.3:** The second method in selected song controller will be CreateSelectedSongRecord(). This method will receive an input from the user of the selected song entry. These attributes include track, artist, album, and playlist. The method will then make a call to the selected song service and post this new entry into the database.
  - **1.2.4:** The third method in the selected song controller will be DeleteSongSelection(). This method makes a call to the selected song service and deletes all current entries in the selected songs table within the database.
- **1.3.0:** Music service will contain a service called song service. Song service will contain any additional business logic needed during requests before passing on to the repository layer.
  - **1.3.1** Song service will inherit from an interface called IMusicService. This gives song service template it needs to satisfy for all its actions. IMusicService contains four functions: GetAsync(),GetAsync(recordNumber), CreateAsync(entry), DeleteAsync(recordNumber).
  - **1.3.2** The first method song service implements is GetAsync(). This method makes a call to the music repository to fetch a list directly from the database of all current entries in the music table.
  - **1.3.3** The second method song service implements is called GetAsync(recordNumber). This method makes a call to the music repository to fetch the music entry from the database with the corresponding record number entered by the user.
  - **1.3.4** The third method song service implements is called CreateAsync(entry). This method makes a call to the music repository to create a new music entry within the music table of the database. The entry is the input the user has passed in with the following attributes: track, artist, album, playlist.
  - **1.3.5** The fourth method song service implements is called DeleteAsync(recordNumber). This method makes a call to the music repository to delete the music record with the inputted record number from the user.
- **1.4.0:** Music service will contain a service called selected song service. Selected song service will contain any additional business logic needed during requests before passing on to the repository layer.
  - **1.4.1** Selected song service will inherit from an interface called ISelectedSongService. This gives song service template it needs to satisfy for all its actions. IMusicService contains three functions: GetSelectedSongs(), CreateSongRecord(entry), DeleteAsync().
  - **1.4.2** The first method song service implements is GetSelectedSongs(). This method makes a call to the selected song repository to fetch a list directly from the database of all current entries in the selected song table.
  - **1.4.3** The second method selected song service implements is called CreateSongRecord(entry). This method makes a call to selected song repository to create a new entry in the selected song table within the database. The song entry attributes are entered in by the user and include: track, artist, album, playlist.
  - **1.4.4** The third method selected song service implements is called DeleteAsync(). This method makes a call to the selected song repository and deletes all rows within selected song table in the database.
- **1.5.0:** Music service will contain a repository layer named Music Repository. This layer will interact with the database directly.
  - **1.5.1** Music Repository will inherit from the interface IMusicRepository. IMusicRepository contains 4 functions: GetAsync(), GetAsync(recordNumber), CreateAsync(entry), Delete(entry).
  - **1.5.2** The first method music repository implements is GetAsync(). This method makes a call to the database directly to fetch all entries in the music table and then returns the list.
  - **1.5.3** The second method music repository implements is GetAsync(recordNumber). This method makes a call to the database directly to fetch the entry that corresponds to the record number entered in by the user. The method then returns the entry.
  - **1.5.4** The third method music repository implements is CreateAsync(entry). This method makes a new entry directly into the database. The entry is the music object entered in by the user and passed through the service layer to the repository. The new entry is added to the music table and then returned.
  - **1.5.5** The fourth method music repository implements is Delete(entry). This method deletes the music entry that is passed in through the service layer once it’s found by it’s record number that the user entered in. This method interacts directly with the database to remove the entry from the music table. The method then returns true or false if entry was deleted successfully.
- **1.6.0:** Music service will contain a repository layer named Selected Song Repository. This layer will interact with the database directly.
  - **1.6.1** Selected Song Repository will inherit from the interface ISelectedSongRepository. ISelectedSongRepository contains 3 functions: GetAsync(), CreateAsync(entry), Delete(entries).
  - **1.6.2** The first method selected song repository implements is GetAsync(). This method makes a call to the database directly to fetch all entries in the selected song table and then returns the list.
  - **1.6.3** The second method selected song repository implements is CreateAsync(entry). This method makes a new entry directly into the database. The entry is the selected song object entered in by the user and passed through the service layer to the repository. The new entry is added to the selected song table and then returned.
  - **1.6.4** The third method music repository implements is Delete(entries). This method deletes the selected song list that is passed in through the service layer. This method interacts directly with the database to remove all entries from the selected table. The method then returns true or false if entry was deleted successfully.

### Recommendation Service

- **1.0.0:** Recommendation service will contain three specific files needed one is the Flask webapp, recommendation model and dataset.
  - **1.0.1:** The first file is: data.csv file sourced from Kaggle. This is the data our recommendation model will consumer and “train” on.
  - **1.0.2:** The second is main.py. This file contains the recommendation model.
  - **1.0.3:** The third is recommendationService.py. This file is where we implement our Flask web app service that communicates with the UI.
- **1.1.0:** The recommendation model will first need to open and read all the lines of data from the csv file we are utilizing as a database for the model to make it's predictions on.
  - **1.1.1:** We then need to clean the data so the model will be able to digest it and its easier to work with.
  - **1.1.2:** The file will also contain a method called euclidean_matrix(data, numberOfRecommendations, song, artist). The purpose of this method is call the model and get recommendation outputs the model generates from the algorithm it utilizes. The inputs that are needed to be passed in are the data itself from the csv file, number of recommendations wanted, song title, and artist. The method then returns the printed text of the song recommendation(s) it has made.

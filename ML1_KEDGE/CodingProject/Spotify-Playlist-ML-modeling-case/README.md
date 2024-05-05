![image](https://github.com/Jhonnatan7br/Spotify-Playlist-ML-modeling-case/assets/104907786/6dfb70de-2b39-4a74-b344-bf324f926fa6)

>[!TIP]
> This is a simplified representation of how a recommendation system can work, to put it in production it can be optimized with other frameworks or more complex models

# Project	 

The distribution of this project is the following, the models work on predicting 'top_year' of songs and 'user' preferences

![image](https://github.com/Jhonnatan7br/Spotify-Playlist-ML-modeling-case/assets/104907786/7e70f51d-315e-443f-a1b4-0b7b48262708)

### Context	

Music streaming services have changed the way we listen to music. Platforms like Apple Music and Spotify allow us to enjoy music anytime and anywhere. You can create your playlists, share them with your friends, and even share your subscriptions with family.
You are responsible for managing multi-user accounts, also known as family accounts. These accounts are associate with a single subscription for multiple users, who retain the ability to create their own playlists and access personal music statistics.

On the morning of November 21, Spotify's servers were attacked by hackers. The hackers deleted users' Top-of-the-Year playlists from family accounts. These users find themselves faced with a huge playlist that mixes everything. If users on the same family account have exactly the same musical taste, that's fine. But who would listen to exactly the same thing as their parents or roommates?

Fortunately, you were able to recover some of the deleted data from Spotify's servers. The recovered data contains parts of the Top-of-the-Year playlists of different users. But some songs from the huge mixed playlist are still missing from the recovered data.
Your mission is to reconstruct each user's Top-of-the-Year playlists for each year.

### Data
	 
- First, you have the single playlist that mixes everything: mixed_playlist.csv
- Some songs in this CSV file have already been labeled with the corresponding user and top year according to the recovered data.
- Some songs are missing from the recovered data, so the user and top year remain unkown.
- Then, you have the recovered parts of the Top-of-the-Year playlists of different users.
- CSV files in the recovered_data folder.

These playlists are not complete.
You need to reconstruct each playlists.
For each song, your team created a number of characteristics to describe this song. These characteristics can also be found in every CSV file.

### Tasks

Reconstruct the Top-of-the-year playlists for different users.
As a data analyst, your team also needs to develop algorithms that recommend the next song to users. The song the user is currently listening to is an important reference. The user's music taste in previous years can also be used as a basis for recommendations. Please suggest several characteristics of song that can be used as input features for the recommendation algorithm and justify your proposal.

#### Note: Before starting 

It is important to notice that every single data extraction from mixed playlist were made taking into account the following location of the file, inside of a folder called 'data'

mixed_playlist = pd.read_csv('data/mixed_playlist.csv')

![image](https://github.com/Jhonnatan7br/Spotify-Playlist-ML-modeling-case/assets/104907786/8297b43c-5b37-4126-8f6b-6bdc3d7b7a43)

The final output will be a folder called 'Playlists' with all the playlists for each user and each year, with the same structure as 'recovered_data' folder

##### Users music "taste", described with a 3D PCA (Principal componen analysis) 

![image](https://github.com/Jhonnatan7br/Spotify-Playlist-ML-modeling-case/assets/104907786/2aa30e05-f9f8-4dac-8781-0f1c92851244)

- KMeans Clustering (K=6): The KMeans algorithm has identified 6 distinct groups within the data. Each group is represented by a different color on the plot. The algorithm tries to minimize the variance within each cluster and maximize the variance between clusters.

- PCA 3D Projection: The PCA has reduced the dimensionality of the dataset to the three most significant components, which are plotted along the three axes (X, Y, Z) of the graph. This type of reduction is useful to visualize high-dimensional data in three dimensions.

- Users' Music "Taste": The clusters likely represent different groups of users with similar music preferences. For example, all users in the red cluster may have similar tastes, which are different from those in the blue cluster, and so on.

Value Generation: This visualization generates value by providing insights into user behavior and preferences. By understanding the different 'tastes' or segments, recommendations can be personalized, marketing strategies can be more targeted, and overall user engagement can be improved. For music streaming services, such analyses are crucial for curating personalized playlists and improving the user experience. This type of data visualization and analysis is quite valuable for businesses that rely on user segmentation and personalization, such as music streaming services, to improve their product offerings and user experience.

At the end it was proposed an accesing to the users playlist throught dictionaries 

![image](https://github.com/Jhonnatan7br/Spotify-Playlist-ML-modeling-case/assets/104907786/84930922-2be4-4fc5-88b3-351fd6ec1d1b)


# Movie-Recommendations-TF

This repository hosts the code used to make machine learning model using Collaborative Filtering using the provided dataset, ml-latest-small.zip which contains links.csv, tags.csv, ratings.csv, and movies.csv files. 

To produce a machine learning model that provides recommendations for a film that has never been watched by the user using the Collaborative Filtering method. Then we will use a dataset containing each user's assessment of the movies they review to achieve our goals. In the end, this machine learning model will provide a recommendation value for each movie that has not been seen by the user, starting from the smallest value, which is not feasible to be recommended to users, to the largest value, which is very feasible to be recommended to users.


## Installation

This project can basically be run on any computer by opening the main.ipynb file with the desired notebook (Example : Jupyter Notebook, Google Colaboratory, Kaggle Notebook, etc.)

But if you want to develop it again with the same settings as the developer had during the production process. Then you can create a virtual environment (You can use other methods, the methods below are not required to be followed!)

```bash
python3 -m venv venv
```

Activate the virtual environment

```bash
. venv/bin/activate
```

Install the required packages for these project.

```bash
pipe install -r requirement.txt
```

## Usage

Create and then save the machine learning model for further use

```python
tf.keras.models.save_model(
    model,
    export_path,
    overwrite=True,
    include_optimizer=True,
    save_format=None,
    signatures=None,
    options=None
)
```

Give top 10 movie recommendations to a user (In this case we choose randomly)
```python
print("Showing recommendations for user : {}".format(user_id))
print("====" * 9)
print("Movies with high ratings from user")
print("----" * 8)
top_movies_user = (
    movies_watched_by_user.sort_values(by="rating", ascending=False)
    .head(5)
    .movieId.values
)
movie_df_rows = movie_df[movie_df["movieId"].isin(top_movies_user)]
for row in movie_df_rows.itertuples():
    print(row.title, ":", row.genres)

print("----" * 8)
print("Top 10 movie recommendations")
print("----" * 8)
recommended_movies = movie_df[movie_df["movieId"].isin(recommended_movie_ids)]
for row in recommended_movies.itertuples():
    print(row.title, ":", row.genres)
```

Result of the above code:
```

Showing recommendations for user : 474
====================================
Movies with high ratings from user
--------------------------------
Fugitive, The (1993) : Thriller
Remains of the Day, The (1993) : Drama|Romance
West Side Story (1961) : Drama|Musical|Romance
X2: X-Men United (2003) : Action|Adventure|Sci-Fi|Thriller
Spider-Man 2 (2004) : Action|Adventure|Sci-Fi|IMAX
--------------------------------
Top 10 movie recommendations
--------------------------------
Living in Oblivion (1995) : Comedy
Fear and Loathing in Las Vegas (1998) : Adventure|Comedy|Drama
Lock, Stock & Two Smoking Barrels (1998) : Comedy|Crime|Thriller
Boondock Saints, The (2000) : Action|Crime|Drama|Thriller
Snatch (2000) : Comedy|Crime|Thriller
In Bruges (2008) : Comedy|Crime|Drama|Thriller
Dark Knight, The (2008) : Action|Crime|Drama|IMAX
Inglourious Basterds (2009) : Action|Drama|War
Toy Story 3 (2010) : Adventure|Animation|Children|Comedy|Fantasy|IMAX
Paperman (2012) : Animation|Comedy|Romance
```

## Further Update

This repository is very useful for further development, such as the application of this machine learning model as a movie recommendation for a movie sales business, or it can be used as a recommendation system for a website that provides many films, both free and paid, that can be watched by users.

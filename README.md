# Django DRF Elasticsearch
1. [Install Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) if you haven't already and make sure it is running on port `9200`.

2. Create and activate a virtual environment:

    ```sh
    $ python3 -m venv venv && source venv/bin/activate
    ```

3. Install the requirements:

    ```sh
    (venv)$ pip install -r requirements.txt
    ```

4. Apply the migrations:

    ```sh
    (venv)$ python manage.py migrate
    ```

5. Populate the database with some test data by running the following command:

    ```sh
    (venv)$ python manage.py populate_db
    ```

6. Create and populate the Elasticsearch index and mapping:

    ```sh
    (venv)$ python manage.py search_index --rebuild
    ```

7. Run the server

    ```sh
    (venv)$ python manage.py runserver
    ```

8. Test Elasticsearch with the following queries:

     - [http://127.0.0.1:8000/search/user/mike/](http://127.0.0.1:8000/search/user/mike/) - should find the user 'mike13'
     - [http://127.0.0.1:8000/search/user/jess_/](http://127.0.0.1:8000/search/user/jess_/) - should find the user 'jess_'
     - [http://127.0.0.1:8000/search/category/seo/](http://127.0.0.1:8000/search/category/seo/) - should find the category 'SEO optimization'
     - [http://127.0.0.1:8000/search/category/progreming/](http://127.0.0.1:8000/search/category/progreming/) - should find the category 'Programming' (:warning: notice the typo)
     - [http://127.0.0.1:8000/search/article/linux/](http://127.0.0.1:8000/search/article/linux/) - should find the article 'Installing the latest version of Ubuntu'
     - [http://127.0.0.1:8000/search/article/java/](http://127.0.0.1:8000/search/article/java/) - should find the article 'Which programming language is the best?'
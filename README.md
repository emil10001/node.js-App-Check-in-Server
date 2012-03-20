This app is intended to allow a developer to manage an independently distributed app, where the developer wants to keep track of users and make sure that everyone is running the latest version. This app is built using node.js and requires the db-mysql library to be installed.

This app connects to a Mysql database with the following schema:

emails:
    +-------+--------------+------+-----+---------+----------------+
    | Field | Type         | Null | Key | Default | Extra          |
    +-------+--------------+------+-----+---------+----------------+
    | id    | int(11)      | NO   | PRI | NULL    | auto_increment |
    | email | varchar(200) | YES  |     | NULL    |                |
    | count | int(10)      | NO   |     | 0       |                |
    +-------+--------------+------+-----+---------+----------------+

versions:
    +---------------+--------------+------+-----+---------+----------------+
    | Field         | Type         | Null | Key | Default | Extra          |
    +---------------+--------------+------+-----+---------+----------------+
    | id            | int(11)      | NO   | PRI | NULL    | auto_increment |
    | current       | tinyint(1)   | NO   |     | 0       |                |
    | version       | varchar(5)   | YES  |     | NULL    |                |
    | download_link | varchar(100) | YES  |     | NULL    |                |
    +---------------+--------------+------+-----+---------+----------------+

Query:
curl -i http://pind.feigdev.com:3000/check_version

Result:
HTTP/1.1 200 OK
Content-Type: text/json
Connection: keep-alive
Transfer-Encoding: chunked

[{"id":1,"current":true,"version":"0.0.1","download_link":"http://files.feigdev.com/pind_beta.apk"}]

Query:
curl -i http://pind.feigdev.com:3000/check_email?email=test@test.com

Result:
HTTP/1.1 200 OK
Content-Type: text/json
Connection: keep-alive
Transfer-Encoding: chunked

{"id":0,"affected":1,"warning":0}


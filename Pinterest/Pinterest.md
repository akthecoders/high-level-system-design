# System Design Pinterest


Functional Requirement
Add New Board
List all my boards
View a board via Id
    permission
    no clone, comment, like
- timeline
    Eventual Consistent
- Share
    - Individually add or remove user
- List all boards shared with me
    - sort shared time

Non Functional Requirement
    Auth management, 
    Security


Functional Requirement
- Add New Board - addNewBoard(boardObject) boardId, (Board Service)
- List All my Boards - getBoardList(); Boards List (Board Service)
- View a board via Id - getBoard(boardId); Boards Object (Board Service)
- timeline - getTimeLine(); TimeLine Object with multiple boards  (Timeline Service)
- Share - shareBoard(userIds); Succcess/ Failure (Board Service)
- Get boards shared with me - getSharedBoardsWithMe() Board List (Board Service)

Non Functional Requirement
- Authentication
- Security


Scaling
Users
    100 M users
    
    80 M users aer active daily

    20 M users will add board (Write)
    80 M users will read board (Read) per day

    Per hr = 80 M users / 24 hrs = 3.3 M  users per hr => 55 K users / min => 916 users/ second 
    Bandwidth required for read
        Let us assume each request consume => 500 KB
        916 * 500 KB = 30 MB / second (approx)

    Let us assume Boards
    20 M users will add boards

    Per hr = 20/24  = 90 K users hr => 90 K per min => 1 user / second will upload a board

    Let us assume 
        Link
        Image Max size = > 500 KB
        Meta Data

    Let us say this data is of 700 KB
    1 MB per second is required

CAP Theorem 
CP => Consistency and Partition
=> Whenever user will add board, it should get updated to all the servers in world
    which will need locking of all the dbs for each transaction, until everyone is updated.

TradeOff => Each board addition will take more time.

AP => Availabitliy and Partition
    TradeOff => The data might not be abailable absolutely valid, It would take some time to update all the caches and dbs worldwide.


What DB should we choose 
SQL and NoSQL

1) We don't need all ACID properties
2) It is ready heavey
3) Schemaless as well

We can go with NoSql => MongoDB

Board
    userId
    Links (Array of Ids)
    ImageURLs (Array of URLs where image is stored)
    MetaData
    OtherField

Links
    linkId
    userId
    originalURL
    hashedURL
    metadata

Share
    userId
    sharedWith
    boardId
    MetaData
    OtherField


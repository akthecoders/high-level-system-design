# TikTok

## Functional Requirement
1. User Profile
    - createProfile(profileObject) : profileId
    - updateProfile(updateProfileObject): statusCode of 200,400,500
    - getProfile(): profileObject
2. Upload Videos
    - uploadVideo(videoObject): statusCode of 200,400,500
3. View Videos
    - getVideo(videoId): videoObject
4. Follow/Following
    - getFollowers(): followersObjectList
    - getFollowing(): followingObjectList

## Non Functional Requirement
1. Authentication
2. Security


## Scaling
Users:
    100 M users daily
    
    20 M are active user daily
    17 M users are putting up the view video requests
        17 M daily active => 700 K users/ hr =>  194 users /sec requesting for videos
        Bandwith Required Based on Video Sizes: 
        Let us take the highest quality stream we are doing => 
        30 MB 
        Since we have divided it into chunks and are providing the video as bit rate streaming
        So Let us assume each chunk will be of 1 MB
        1 M user => 1M MBs of bandwidth per day. 10 K GB, 
        10 TB * 30 => 300 TB of bandwidth per day.

    1 M users are querying about other resource other requests
        Let us assume that each request is of 20 KB
        40 K users / hr => 600 K users / min => 10 requests / sec

        Bandwidth required: 20 KB * 10 users / sec => 200 KB /sec need to be looked into.

    2 M users are actively uploading the data into our system.
        Let us say there will be multiple format but for convinience we will take 3 formats
        1) Low Quality - 1 MB
        2) Medium - 10 MB 
        3) Hight Quality - 30 MB

        User will be uploading any one quality video out of these, but we wil take the highest quality for calculation and predictions.

        2 M users 
        80 K users/ hr => 1200 Users / min => 20 video uploads / sec request
        Bandwidth => 20 * 30 MB => 600 MB / sec.

        Space Required => 30 MB * 20 = > 600 MB in each sec.
        1 M users => 30 MB * 1 M => 30M MBs space is required => 30000 GB => 20TB space for 1 M users daily.

## What type of system is this ?

1) There are more users requesting for videos as compared to the uplaod . 
So this is a Read Heavy System.
Since we do not want consistency very much a video uploaded at some place can be dealyed for some time.
So as per the CAP Theorem this is a 
"AP system"

1) We don't need ACID properties
2) Read heavy system
3) Schemaless as well.

We can choose NOSQl DB with MongoDB as this is just Read Heavy.
And for the storage we can choose Amazon's S3 Object Store.

## DB Design

UserProfile
id: String
userId: String
firstName: String
lastName: String
..otherFields

uploadedVideo
userId: String
videoURL: String
format: String
quality: String

followersfollowingMapper
userId: String
followingId: Array of IDs

# 3D Scanning Method for Human

3D scanning is the act of mapping an object, structure, or area, and describing it in the form of x, y, and z coordinates - a format known as a “point cloud”.

Basically it can be divided into 2 main approaches.

1. Photogrammetry
2. Laser scanning

## Photogrammetry

There are 2 main approaches for 3D reconstruction by using photogrammetry. They are SLAM(Simultaneous localization and mapping) and SFM(Structure from Motion)

 They have the following key differences in practice.

 1. Realm-time efficiency
   - SLAM is supposed to work in real-time on an ordered sequence of images
   - SFM approaches often have to work on an unordered set of images often computed in the cloud with little to no time constraints and might employ different cameras (e.g. reconstructing notable landmarks, Eiffel tower perhaps from community photos)
 2. Scalability
   - SFM approaches have been scaled to work on the “planet” level. Researchers have applied SfM to Google Street View photos simultaneously reconstructing some portion of our whole inhabited planet
   - large scale visual SLAM is typically restricted to trajectories of a few kilometers.
 3. Imageset requirement
   - SLAM always works with ordered image set
   - SFM usually uses unordered image set. Since you don’t have an ordered set of images in SfM, and your image set (e.g. all images of Rome available on Flickr) might be huge, its a challenge to retrieve near-by images, and add images one by one to a growing graph while accounting for potential outlier images so that robust reconstruction maybe performed.

### SFM (Structure from Motion)

Given a large photo collection of a single outdoor structure (such as a large theater / stadium), build the 3D model of the structure and determine the posture of each camera. This collection of photographs is processed off-line, and the time required for large-scale structural reconstruction ranges from hours to days.

#### Test environment

A experiment to reconstruct a jar as following:

![image](https://image.ibb.co/jJmn0m/Screen_Shot_2017_10_26_at_2_14_47_PM.png)

#### Hardware and software

Intel i5-3230M CPU 8GG ROM

[VisualSFM](http://ccwu.me/vsfm/)

#### Time and storage cost

Image amount: 65

Image quality: 1024 * 768

Photographing time: 10min

Processing time: 30min

Temporary file size: 350M


#### Final result

![image](https://image.ibb.co/k1XALm/Screen_Shot_2017_10_26_at_2_23_36_PM.png)


### SLAM(Simultaneous localization and mapping) reconstruction

With in SLAM solution there are the following solutions. Tango is a basically a Dense visual SLAM using RGB-D Method and provides a stable estimation result by combining internal sensor information. In addition Apple's ARKit and Goolge's ARCore is basiclly a LSD-SLAM method.

First Header                | Second Header
----------------------------|-----------------------------
Content from cell 1         | Content from cell 2
Content in the first column | Content in the second column

Name | Method | Map density | Global optimization | Loop closure
-----| ------ | ----------- | ------------------- | -------------
[Mono-SLAM](https://scholar.google.com/scholar?q=Davison%20AJ%20%282003%29%20Real-time%20simultaneous%20localisation%20and%20mapping%20with%20a%20single%20camera%20In%3A%20Proceedings%20of%20International%20Conference%20on%20Computer%20Vision%2C%201403%E2%80%931410.)  |  Feature |  Sparse |  No | No   
[PTAM](https://scholar.google.com/scholar?q=Klein%20G%2C%20Murray%20DW%20%282007%29%20Parallel%20tracking%20and%20mapping%20for%20small%20AR%20workspaces%20In%3A%20Proceedngs%20of%20International%20Symposium%20on%20Mixed%20and%20Augmented%20Reality%2C%20225%E2%80%93234.) | Feature | Sparse | Yes | No
[ORB-SLAM](https://scholar.google.com/scholar_lookup?title=ORB-SLAM%3A%20a%20versatile%20and%20accurate%20monocular%20SLAM%20system&author=R.%20Mur-Artal&author=JMM.%20Montiel&author=JD.%20Tard%C3%B3s&journal=IEEE%20Trans%20Robot&volume=31&issue=5&pages=1147-1163&publication_year=2015) | Feature | Sparse | Yes | Yes
[DTAM](https://scholar.google.com/scholar?q=Newcombe%20RA%2C%20Lovegrove%20SJ%2C%20Davison%20AJ%20%282011%29%20DTAM%3A%20dense%20tracking%20and%20mapping%20in%20real-time%20In%3A%20Proceedings%20of%20International%20Conference%20on%20Computer%20Vision%2C%202320%E2%80%932327.) | Direct | Dense | No | No
[LSD-SLAM](https://scholar.google.com/scholar?q=Engel%20J%2C%20Sch%C3%B6ps%20T%2C%20Cremers%20D%20%282014%29%20LSD-SLAM%3A%20large-scale%20direct%20monocular%20SLAM%20In%3A%20Proceedings%20of%20European%20Conference%20on%20Computer%20Vision%2C%20834%E2%80%93849.) | Direct | Semi-dense | Yes | Yes
[SVO](https://scholar.google.com/scholar?q=Forster%20C%2C%20Pizzoli%20M%2C%20Scaramuzza%20D%20%282014%29%20SVO%3A%20fast%20semi-direct%20monocular%20visual%20odometry%20In%3A%20Proceedings%20of%20International%20Conference%20on%20Robotics%20and%20Automation%2C%2015%E2%80%9322.) | Semi-direct | Sparse | No | No
[DSO](https://scholar.google.com/scholar?q=Engel%20J%2C%20Koltun%20V%2C%20Cremers%20D%20%282016%29%20Direct%20sparse%20odometry.%20CoRR.%20abs%2F1607.02565.) | Direct | Sparse | No | No
[KinectFusion](https://scholar.google.com/scholar?q=Newcombe%20RA%2C%20Izadi%20S%2C%20Hilliges%20O%2C%20Molyneaux%20D%2C%20Kim%20D%2C%20Davison%20AJ%2C%20Kohi%20P%2C%20Shotton%20J%2C%20Hodges%20S%2C%20Fitzgibbon%20A%20%282011%29%20KinectFusion%3A%20real-time%20dense%20surface%20mapping%20and%20tracking%20In%3A%20Proceedngs%20of%20International%20Symposium%20on%20Mixed%20and%20Augmented%20Reality%2C%20127–136.) | RGB-D | Dense | Yes | Yes
[ElasticFusion](http://www.roboticsproceedings.org/rss11/p01.pdf) | RGB-D | Dense | Yes | Yes
[SLAM++](https://scholar.google.com/scholar?q=Salas-Moreno%20RF%2C%20Newcombe%20RA%2C%20Strasdat%20H%2C%20Kelly%20PHJ%2C%20Davison%20AJ%20%282013%29%20SLAM%2B%2B%3A%20simultaneous%20localisation%20and%20mapping%20at%20the%20level%20of%20objects%20In%3A%20Proceedings%20of%20IEEE%20Conference%20on%20Computer%20Vision%20and%20Pattern%20Recognition%2C%201352%E2%80%931359.) | RGB-D | Dense | Yes | Yes
[Dense visual SLAM](https://scholar.google.com/scholar?q=Kerl%20C%2C%20Sturm%20J%2C%20Cremers%20D%20%282013%29%20Dense%20visual%20SLAM%20for%20RGB-D%20cameras%20In%3A%20Proceedings%20of%20International%20Conference%20on%20Intelligent%20Robots%20and%20Systems%2C%202100%E2%80%932106.) | RGB-D | Dense | Yes | Yes

#### Test environment

A 10 sqm living room

#### Hardware and software

Asus Zenfone Tango AR

Airsquire capturing tool

#### Time and storage cost

Cost: $800

Capturing time: 5 min

Processing time: real-time

File size: 50 MB

Accuracy: 2.5cm


## Laser scanner

Three-dimensional laser scanning can be used to collect spatial location of points rapidly and abundantly, and obtain three-dimensional coordinates of the target surface.

#### Test Environment

The rock shelter is located in a region known as West Angeles in Western Australia. It is approximately 50m long, 20m deep and between 1.6 and 3m high. An interactive 360x180 panorama of the site can be experienced below.

![image](https://preview.ibb.co/hTgET6/day2pano3s.jpg)

#### Hardware and software

Laser scanner -- Leica C10(green light, 532nm)

#### Time and storage cost

Cost: 27000.00 USD

Capturing time: 1 day

Processing time: Several days

File size: Several GB

Accuracy: 10m/2mm；25m/3.5mm for Faro Focus S 150/350


## Credit

1. https://www.quora.com/What-is-the-difference-between-SfM-and-Visual-SLAM
2. http://blog.csdn.net/linczone/article/details/46237197
3. https://developers.google.com/tango/apis/c/reconstruction/reference/
4. https://link.springer.com/article/10.1186/s41074-017-0027-2
5. http://paulbourke.net/miscellaneous/laservs3d/
6. http://www.itailai.com/html/article/620.html

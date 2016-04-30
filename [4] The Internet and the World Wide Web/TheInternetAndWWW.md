# Bitwisr: i2CS
The Internet: that amazingly diverse collection of web sites, photoshopped images, and adorable cat videos that is ever pervasive in today’s society. Quite possibly, the Internet has been the most profoundly impactful development of the last 50 years, changing the way we interact with other people, shop for things, and do research for that project that you just remembered is do next Monday. But what exactly is the Internet, and how do our computers allow us to use it every day?

## Lesson 04: The Internet and the World Wide Web
### Required Materials:
* [ ] Your computer
* [ ] Access to the Internet

### Objectives:
* [ ] Know what the Internet and the World Wide Web are
* [ ] Understand what the terms **router**, **IP Address**, **packet**, **protocol**, **server**, and **DNS** mean.
* [ ] Understand and explain how information from your computer can reach a website and vice-versa
* [ ] Be able to think about the impact the Internet has had on the world, and what impacts it might have

### What the Internet and World Wide Web Are
What we know today as ‘The Internet’ is actually a massive, globally accessible collection of computer networks. This meta network allows for the access of information by computers that are connected to it. In practice, this was first realized in ARPANET, a collection of academic and military networks developed in the 1970s<sup>[1]</sup>,  but in theory the idea of a global interconnected network for information sharing is much older.

The main use of the Internet, at least by most people, is to access information on the World Wide Web. The World Wide Web is the network that connects information on computers connected to the Internet, and was developed years after the Internet, at the European Research Center CERN by Tim Berners-Lee
<sup>[2]</sup>. By using the World Wide Web, information can be accessed and referenced in a dynamic and useful way.


### How We Interact with the Internet
When you go online to watch videos on YouTube or read articles on Wikipedia, the process you usually see goes something like this:
1. Types in name of website
2. Hits enter
3. Website loads (very noticeable when the Internet is ‘slow’)
4. Website appears in browser

What happens behind the scenes is a little bit more complicated.

#### Where the Internet Is
First, it is important to understand that websites do not exist in some kind of magical ether known as the ‘cloud’ - websites are data stored on **servers**, computers dedicated to receiving requests for data and sending it back out over the internet<sup>[3]</sup>. So, when you are trying to watch a video on YouTube, your computer is sending requests to a YouTube server saying something like “Hey! I see that you have a video there. Might you show it to me?”, to which the YouTube server says “Why I’d be delighted to!”, and sends that video back to your computer.

#### Protocols and Packets
If you have ever used a slow internet connection, you know that it can take a long time to load pictures or stream high definition video. The main reason for this is that there is a lot of information to load. This same problem affects all data on the internet, even paragraphs of text. Confronted with this, scientists needed a way to make the exchange of information across their new invention practical. One of the methods they used to accomplish this is **packet encapsulation**.

**Packet encapsulation** essentially means breaking down big pieces of information into smaller pieces known as packets. Imagine that Alice has a life-sized picture of her cat, which she wants to send to her friend Bob. Try as Alice might, her picture just won’t fit into her mailbox - its to large and unwieldy. Her solution to this conundrum is to turn her picture into a puzzle and mail it piece by piece to Bob through the mail.

While this solves the problem of how to get her lovely picture to Bob, she has now inadvertently created a new problem - Bob now has to spend time trying to put the puzzle back together. To remedy this situation, Alice decides that along with the puzzle piece, each envelope she sends to Bob will also include information about where the piece fits into the puzzle as a whole. Now when Bob gets her message in the mail, he can put the puzzle piece right where it belongs, even if the pieces aren’t send in order. This is how **protocols** solve the problem of how packets are sent over the Internet. They ensure that packets can be broken apart and reassembled when transmitted. Packets also standardize communication between computer networks -  providing a ‘common language’ for how different networks can talk to each other. But the Internet is a big place, with billions of connected computers. How does your computer know which servers are YouTube servers and how does the YouTube server know where to send the video packets? In the same way that people have geographic addresses that tell you where to find their house, so too do computers.

#### IP Addresses
Instead of referring to computers by their physical location, networks refer to computers based on their **IP Address**, a unique number that is assigned to each device connected to the Internet. When you want to access a website (a server), your computer uses the server’s IP address to access it, and the server in turn uses your computer’s IP address to send back the information in the same way that you might exchange letters with someone by sending envelopes with and destination and return addresses.<sup>[4]</sup> So what exactly does an IP address look like?

Today, IP addresses come in two main variants: IPv4 and IPv6 (the ’v’ stands for version). Although IPv4 is technically the fourth version of IP address, it was the first one released for ARPANET and is still widely used. In practice, an IPv4 address looks something like ```127.0.0.1``` - that is, a series of 4 numbers, each separated by a period. The numbers can be anywhere from ```0``` to ```255```.

Why 255? you may ask. The answer has to do with binary data, that is 1s and 0s, and the relationship between the size of data and the ability to move it quickly and efficiently across computer networks. Unlike humans, which for the most part have adopted a base 10 number system (called decimal), computers think only in terms of binary digits: 1 or 0, on or off, electricity or no electricity. This means that all numbers are stored, not in base 10 but in base 2 - binary. To a computer, the numbers are not ```127.0.0.1```, but ```1111111.0.0.1``` - with each number being translated into its binary equivalent. But there’s a problem - those periods between numbers don’t actually exist; they are only there to make the address readable to humans. Without the separators, the only way for a computer to know where one number ends and the other number begins is to know how long each number is - how many digits it has. They do this by making each number a fixed number of digits by adding 0s to the beginning of numbers until each number is the same length.

```
1 (1 digit) = 00000001 (8 digits)
127.0.0.1 = 01111111.00000000.00000000.00000001 = 01111111000000000000000000000001
```

So, how long can each number be in binary? Well, the longer the number is, the more IP addresses there can be, so why don’t computers just use insanely long numbers? Because it increases the size of the data - slowing down communication and making it less efficient. When designing IPv4, engineers decided on a compromise of 4 numbers, each with 8 binary digits (also called a byte, of gigabyte fame) - long enough that there can be a substantial number of addresses but short enough that the communication speed isn’t too slow. So, these addresses can range from ```00000000.00000000.00000000.00000000``` to ```11111111.11111111.11111111.11111111```, or from ```0.0.0.0``` to ```255.255.255.255```.

With 4 numbers, each 8 digits, this means that there are a total of 32 digits of value, yielding a maximum of 2<sup>32</sup>, or ```4,294,967,296``` IPv4 addresses. Back in the early 1990s, this seemed like a reasonable limit. In 2015, with billions of people connected to the internet, most with multiple computers, not so much.

To try and delay the inevitable, engineers developed a new technology known as Network Address Translation (NAT)<sup>[5]</sup>. How does it work? Instead of your computer being connected directly to the Internet, it connects through a device called a **router**. You may know this as the thing you have to unplug and replug every time your Internet connection goes down. Instead of assigning every computer a public IP address, you get one public IP address for your router, and your router assigns private IP addresses inside your home network. When any computers on your home network accesses the internet, they first go through the router, which uses its single IP address to connect to the outside world. Effectively, this reduces the number of IP addresses that are needed for multiple devices in the same area.

Unfortunately, this doesn’t stop the root of the problem, which is that as more and more devices connect to the Internet, the number of remaining available IP addresses gets smaller and smaller. Eventually all the IPv4 address were used up, so a new standard known as IPv6 was developed, the v5 having been used by an experimental protocol which didn’t pan out.<sup>[6]</sup> This new kind of IP address looks something like ``` ``` , and allows for 2<sup>128</sup> possible addresses.

#### The URL (Uniform Resource Locater)
Now, if you think that having to remember a 64 digit combination of numbers and letters every time you want to look up something on Google would be a bit tedious, you would be right. This is where URLs come in. URLs are the ‘names’ of websites<sup>[7,8]</sup> that we type into a web browser like ```https://www.google.com/```. Your computer sends this URL to a special type of server called a **Domain Name Server**, a kind of address book of URLs and their matching IP addresses<sup>[9]</sup>. Your router then uses the IP address it receives from the DNS to find the website you wanted.

To review: Your computer is connected to a vast network of computers called the Internet, through which you can access data and references collectively known as the World Wide Web. You are connected to the Internet through your publicly identified router, which keeps track of all the computers on your home network. When you want to look a cat videos or funny GIFs online, your computer sends a message to your router saying “Hello. Can I have the Internet please?”. Your router sends this message to a DNS, gets the IP address of the website you want, and sends a request to the website server, which responds with the requested data. Your router forwards this along to your computer, and all is well.

### What the Internet means
Much of the Internet’s original infrastructure was designed for scientists to share academic information and distribute resources. In the 1960s, the concepts of e-commerce, Wikipedia, YouTube, and Tumblr didn’t exist. Since then, the subsequent growth and development of the Internet has profoundly impacted our lives. Many people cannot remember a time before computers existed, and many have never lived during a time when access to digital information was not omnipresent.

Perhaps the most well-known measure of the internet is instant access to information. Wikipedia, news sites, even Reddit show that the Internet has created a world where many people can access knowledge without needing to really remember it.

Social media is also impactful - Facebook, Twitter, Tumblr, and Snapchat are all services provided by using the Internet. In fact, early on email was one of the things that accounted for much of the traffic online - used by scientists and researchers to communicate data and text.

And of course, no discussion of the Internet would be complete without mention of the many different entertainment services it makes possible. Netflix, Hulu, and YouTube all create a space that provides videos ranging from the educational to the not-so-educational. Downloadable music and ebooks owe their existence to the online networks that many of us take for granted.

#### Who Has Access to the Internet?
For many people in America and Europe, access to the Internet can seem second nature. Of course people can check Facebook, and there really is no excuse for not replying to that email within the hour, is there?

But for many people, this isn’t the case. While the presence of high speed Internet access is ubiquitous for many people in developed countries, only between 2 and 3 billion people are really connected (as of 2015)<sup>[10,11,12]</sup>. While this is certainly a lot of people, most are concentrated in certain areas. For people in countries which do not have the resources or infrastructure to provide access, the Internet is not a part of daily life.

And not all government-regulated internet access is created equal<sup>[13]</sup>. Some countries have highly regulated internet connections, where content is subject to discrimination, censorship, and filters. In the People’s Republic of China, the program of intense censorship and regulation has earned the name ‘The Great Firewall’, and in the U.S. the issue of Net Neutrality has prompted debate and protest.

Finally, there is the issue of content. The presence of English-language content on the Internet is rather dominant<sup>[14,15,16]</sup>, and just a few spoken languages account for the vast majority of content. This means that for people who do not speak English, Russian, or German, the amount of usable information is greatly diminished.

### Recap
* [ ] What is the Internet? The World Wide Web?
* [ ] Explain how information is sent from your computer to another using the Internet.
* [ ] What do you think the advantages of using packets are?
* [ ] How has the Internet changed the way you live your life?
* [ ] How do you think the Internet will change life in the future?
* [ ] What impact do you think the internet has on countries which do not have access to it?

### Assignment
A recent issue in Internet freedom is Network Neutrality - whether or not Internet Service Providers should have the ability to manipulate what kind of content they allow users to access. Find out more about what Net Neutrality means, what ISPs are, and what legislation has been passed or is currently being discussed relating to it. What are Internet Service Providers, how many are there, and which one do you use?

### References
1. [ARPANET (Wikipedia)](https://en.wikipedia.org/wiki/ARPANET)
2. [Word Wide Web (Wikipedia)](https://en.wikipedia.org/wiki/World_Wide_Web)
3. [Where the Internet lives (Google)](www.google.com/about/datacenters/gallery/#/tech/9)
4. [About IP addresses (Google)](https://support.google.com/websearch/answer/1696588)
5. [How Network Address Translation Works (PieterExplainsTech)](https://www.youtube.com/watch?v=QBqPzHEDzvo)
6. [IPv4, IPv6, and IPv5 (Stack Exchange)](programmers.stackexchange.com/questions/185380/ipv4-to-ipv6-where-is-ipv5)
7. [Uniform Resource Locator (Wikipedia)](https://simple.wikipedia.org/wiki/Uniform_Resource_Locator)
8. [What is a URL (Indiana University)](https://kb.iu.edu/d/adnz)
9. [Domain Name System (Wikipedia)](https://simple.wikipedia.org/wiki/Domain_Name_System)
10. [Map of Worldwide Internet Access (The Net Monitor)](https://thenetmonitor.org/map#)
11. [Internet Statistics (Internet Live Stats)](http://www.internetlivestats.com/internet-users/)
12. [Internet.org](https://internet.org/)
13. [Internet Censorship (Wikipedia)](https://en.wikipedia.org/wiki/Internet_censorship)
14. [Languages on the Internet (Wikipedia)](https://en.wikipedia.org/wiki/Languages_used_on_the_Internet)
15. [Online Languages (w3techs)](http://w3techs.com/technologies/overview/content_language/all)
16. [Internet Users by Language](http://people.oii.ox.ac.uk/hanteng/2015/02/24/internet-users-by-language-the-top-20/)

### Resources
* [The Cloud (xkcd)](https://xkcd.com/908/)
* [Who Invented the Internet? And Why? (In a Nutshell – Kurzgesagt)](https://www.youtube.com/watch?v=21eFwbb48sE)
* [The Web Is Not The Net (Vsauce)](https://www.youtube.com/watch?v=scWj1BMRHUA)
* [The First Website](http://info.cern.ch/)
* [What Happens on the Internet Every Second](http://onesecond.designly.com/)
* [what is my ip (Google)](https://www.google.com/search?q=what+is+my+ip)
* [Map of Internet Censorship (Wikimedia)](https://en.wikipedia.org/wiki/Internet_censorship#/media/File:Internet_Censorship_and_Surveillance_World_Map.svg)
* [Internet Censorship by Country (Wikipedia)](https://en.wikipedia.org/wiki/Internet_censorship_and_surveillance_by_country)
* [John Oliver on Net Neutrality (Last Week Tonight)](https://www.youtube.com/watch?v=fpbOEoRrHyU)
* [ViHart on Net Neutrality](https://www.youtube.com/watch?v=NAxMyTwmu_M)
* [CGPGrey on Net Neutrality](https://www.youtube.com/watch?v=wtt2aSV8wdw)
* [Hank Green on Net Neutrality #1](https://www.youtube.com/watch?v=Ou9S3wrHg8c)
* [Hank Green on Net Neutrality #2](https://www.youtube.com/watch?v=mc2aso6W7jQ)
* [Hank Green on Net Neutrality #3](https://www.youtube.com/watch?v=5f3cChVh3UM)

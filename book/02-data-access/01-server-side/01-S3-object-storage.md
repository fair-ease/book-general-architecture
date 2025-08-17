# S3, a cloud filesystem

S3 (Simple Storage Service) is a widely adopted cloud-based object
storage system that allows data to be stored and accessed as discrete
objects, each associated with both the actual data content and metadata.

![](media/image28.png){width="5.008858267716535in"
height="1.407843394575678in"}

[]{#_heading=h.6t96xzkh6pwo .anchor}*Figure 5 - Storage types
comparison*[^3]

Unlike traditional file systems, S3 operates over the HTTP protocol
along with API's, making it highly scalable and accessible across
distributed systems. It supports fine-grained access control, enabling
secure, policy-driven access to individual objects. UCA has provided a
1TB S3 endpoint to help users become acculturated to this technology.

Additionally, S3 API supports HTTP range requests[^4], allowing users or
applications to retrieve specific fragments of a file, using byte
ranges, without needing to download the entire file. This is an
essential feature for large-scale scientific datasets and cloud-native
workflows. This feature is notably used in particular by the Volcano
Space Observatory to optimize access to a specific satellite image from
a TIFF file supplied by Copernicus Data Space Ecosystem.

![](media/image33.png){width="3.6027351268591428in"
height="2.2886679790026245in"}

[]{#_heading=h.ycmdenv04vce .anchor}*Figure 6- HTTP range requests*
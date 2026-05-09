---
title: 'Travelers to Freedom: Methodology'
date: 2026-05-09
permalink: /posts/2026/05/travelers-to-freedom-methodology/
header:
  teaser: "/images/travelers-to-freedom/1863_Johnson-Eastman_A-Ride-for-Liberty.jpg"
tags:
  - travelers to freedom
---
This post explains the methodological challenges of the project and details my data organization.

<h1>Introduction</h1>

<p>Representing the geographic journeys of freedom seekers means confronting the challenge of researching a secret. There are sources from some Underground Railroad participants; for this project, I relied on the records of Sydney Howard Gay and William Still, pivotal members of the anti-slavery networks in New York City and Philadelphia, respectively.<sup><a href="#fn1" id="r1">[1]</a></sup></p>

<h1>Sources</h1>

<p>The most well-known contemporary documentation of the Underground Railroad comes from William Still. As the secretary and chairman of the Pennsylvania Vigilance Committee, Still received almost 1,000 freedom seekers between 1853 and 1861, recording information about each traveller.</p>

<figure>
    <img src="/images/travelers-to-freedom/William-Still.png" width="274px" height="435px">
    <figcaption>William Still, photographed ca. 1852-1860.<sup><a href="#fn2" id="r2">[2]</a></sup></figcaption>
</figure>

<p>Through the combined efforts of scholars James McGowan, William C. Kashatus, Nick Sacco, and Jeremy Mennis, Still’s records of freedom seekers are available as a geocoded database. In this dataset, each data entry row represents one person; the geographic information refers to the place from which they escaped.<sup><a href="#fn3" id="r3">[3]</a></sup></p>

<figure>
    <iframe src="https://urochester.maps.arcgis.com/apps/instant/basic/index.html?appid=82fc2c5d10ba4fc8833312138b5b8ae3" width="900" height="600" frameborder="0" style="border:0" allowfullscreen>iFrames are not supported on this page.</iframe>
    <figcaption>William Still recorded the locations where the freedom seekers who passed through his office had been enslaved.<sup><a href="#fn4" id="r4">[4]</a></sup></figcaption>
</figure>

<p>While this information is useful and interesting, it is more a representation of freedom seeker origins than movement. This is likely due, at least in part, to source availability. Most of Still’s records are available in his book, <i>The Underground Rail Road</i>, which he published in 1872—almost 20 years after he began his work with the Vigilance Committee. Clearly, Still had both impressive record-keeping discipline and an impressive memory—his book is nearly 800 pages—but there are places where he omits information due to lack of source material (helpfully, he straightforwardly announces these cases in the text of his book). The details of freedom seeker narratives are sometimes vague, particularly geographic information.</p>

<p>In New York City, Sydney Howard Gay fulfilled a similar role as William Still did in Philadelphia. Gay edited the National Anti-Slavery Standard newspaper and served as a corresponding officer for the American Anti-Slavery Society.<sup><a href="#fn5" id="r5">[5]</a></sup></p>

<figure>
    <img src="/images/travelers-to-freedom/1860-ca_Sydney-Howard-Gay-Portrait.jpg" width="274px" height="435px">
    <figcaption>Sydney Howard Gay, photographed ca. 1860.<sup><a href="#fn6" id="r6">[6]</a></sup></figcaption>
</figure>

<p>Like Still, Gay kept meticulous records of the freedom seekers who passed through his office (<a href="https://exhibitions.library.columbia.edu/exhibits/show/fugitives/record_fugitives">available in photograph and transcript form from the Columbia University library</a>). Unlike Still, however, Gay never wrote a book, and the details included in his records are often sparser but more clear. The two men also had different record-keeping approaches; Still tended to record more personal details (age, appearance, occupation, literacy), while Gay recorded more details about freedom seekers’ travels. Gay’s records are the basis for this project, with Still’s book and other sources often serving as a supplement.<sup><a href="#fn7" id="r7">[7]</a></sup></p>

<p>The goal of this project is to turn Gay’s records into a geodatabase that visualizes the movement of freedom seekers. The database, at this point, is unfinished. Gay recorded hundreds of stories, and I anticipate that full data analysis will be a multi-year project. Even without a complete dataset, however, some interesting trends emerge, which I explore in the conclusions post. The rest of this post covers database construction and organization.</p>

<h1>Method and data organization</h1>

<p>This database records each known location of each freedom seeker that appears in Gay’s records as a data point. Rather than having each row of data correspond to one person, each row corresponds to one stage of their journey. For example, a hypothetical freedom seeker who escaped from Baltimore, stopped in Wilmington, Philadelphia, New York, Syracuse, and Rochester, and ended up in Toronto, would appear in seven rows of data. Where possible, I have included times and dates of arrivals and departures and transportation information. I have also included the individuals who assisted freedom seekers on their journeys.</p>

<p>I entered the data into an Excel spreadsheet with three primary sheets:</p>

<ul>
  <li><b>Places</b>: a sourced list, with geodata, of places that commonly appear. For example, because every freedom seeker in Gay’s records stops in his office at least once, I included Gay’s office as a listing in the “Places” sheet rather than including the same citation for his office location in the “Source” field for every data point where a freedom seeker stops there.</li>
  <li><b>People</b>: a list of demographic data about every freedom seeker in Gay’s records. With minimal changes, I have followed the format that Jeremy Mennis uses to organize the same type of information from William Still’s records.<sup><a href="#fn8" id="r8">[8]</a></sup></li>
  <li><b>Movements</b>: a list of every identifiable geographic location where freedom seekers in Gay’s records stopped.</li>
</ul>

<p>The “Movements” sheet is the most significant to the project, and requires the most explanation. For each stop on a freedom seeker’s journey, I have recorded data (if available) for the following fields:</p>

<table>
  <tr>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><b>ESCAPE</b></td>
    <td>Identifies the journey partially described in the data row. Hyphenated labels indicate multiple travelers with different last names (ie, "Lewis-Banks"). Single travelers are labeled with their last and first names (ie, "Hill, Simon"). If applicable, family relationships are noted with the appropriate hyphenated or non-hyphenated format (ie, "Johnson family" and "Brown brothers" for related travelers with a single last name, "Cummens-Moody family" for related travelers with differing last names).</td>
  </tr>
  <tr>
    <td><b>LAST_NAME</b></td>
    <td>Identifies listees' surnames.</td>
  </tr>
</table>

<br>

<h1>Estimates and approximations</h1>

<p>Unfortunately, like many historical sources, Gay’s records can’t always offer exactness that allows us to pinpoint the exact location that he references. Without modern GPS (and, in the case of many freedom seekers, literacy), nineteenth-century travelers themselves didn’t always know where they were. I have kept the data entry as consistent as possible, despite some challenges in the following categories:</p>

<h2>Location</h2>

<p>The geographic data is formatted as longitude and latitude. This was fairly easy for locations for which I could find a contemporary address, since most mapping softwares (I used a combination of ArcGIS and Google Maps) provide coordinates as well as addresses. For exact addresses (for example, the <i>National Anti-Slavery Standard</i> office at 138 Nassau St, New York, NY 10038), I included four digits after the decimal in the longitude and latitude coordinates. For locations that correspond to a small region rather than a single address (for example, “Christiana River Landing,” “Broad Street Pier,” or “10th Street, Philadelphia”), I included three digits after the decimal. For large regions such as an entire town or city, I included two digits. I retrieved the longitude and latitude of large regions from Wikipedia’s Geohack program, which provides links to a variety of geographic information (you can view <a href="https://geohack.toolforge.org/geohack.php?pagename=Richmond,_Virginia&params=37_32_27_N_77_26_12_W_region:US-VA_type:city(226610)">the GeoHack page for Richmond, Virginia, here</a> as an example). This provided a more systematic way of choosing coordinates than pulling the longitude and latitude from a random point in the relevant town or city.</p>

<p>In some cases, Gay’s records include geographic references for which I provided no geodata. For example, in August 1855, freedom seeker Elizabeth Banks passed through both Still and Gay’s offices en route to Canada. She had escaped in approximately 1852 and lived in Pennsylvania in the intervening time; news that her former enslaver was searching for her prompted her to leave the country. In this case, I have included geographic coordinates for the location where Banks was enslaved (Easton, Maryland), and for her stops as she traveled north, but not for her residence in Pennsylvania. A set of coordinates for Pennsylvania as a whole would appear in the center of the state, which would be visually misleading without offering any substantial information about Banks’ whereabouts.<sup><a href="#fn9" id="r9">[9]</a></sup></p>

<p>Some geodata is highly speculative. In September 1855, Gay reported that brothers Anthony and Albert Brown, who escaped via sailboat, landed “20 miles above Baltimore, MD.” This record provides a reference, a relative distance, and a direction, which allows for an estimated set of geographic coordinates that is visually illustrative but inexact.<sup><a href="#fn10" id="r10">[10]</a></sup></p>

<p>I have avoided speculating about the more specific locations that Gay might be referring to when he recorded sending or receiving freedom seekers from towns or cities with known Underground Railroad participants unless other sources suggest a specific agent or address.</p>

<h2>Time</h2>

<p>Gay occasionally makes relative references to days rather than listing specific dates. For example, on Wednesday, October 3, Gay recorded that freedom seekers Sam Turner and Wesley Jones had departed Chestertown, Maryland “three weeks ago on Sat[urda]y.” This prompts a chronological question: since Wednesday, September 12, was exactly three weeks before Wednesday, October 3, is Gay referring to the Saturday before September 12 (Saturday, September 8) or the Saturday after (Saturday, September 15)? Although either is technically possible, I have chosen the closer date in this and similar cases; the database therefore indicates that Turner and Jones departed on September 15.<sup><a href="#fn11" id="r11">[11]</a></sup></p>

<p>I have avoided speculating on freedom seekers’ dates of departure from Still and Gay’s offices unless explicitly revealed, although it appears that the majority of travelers left the respective office and city on the same day that they arrived.</p>

<h1>Conclusion</h1>

<p>That is the (slightly dry) gist of how this project has come together. For the more interesting part—what all this data can tell us—see the conclusions post.</p>

<section>
  <p id="fn1"><a href="#r1">[1]</a> <small>Eric Foner, <i>Gateway to Freedom: The Hidden History of America’s Fugitive Slaves</i> (Oxford University Press, 2015), 9–12, 94–108; William Still, <i>The Underground Rail Road</i> (Porter & Coates, 1872).</small></p>
  <p id="fn2"><a href="#r2">[2]</a> <small>Joseph Husted et al., William Still Photograph, 1890, photograph, Ohio History Connection, Wilbur H. Siebert Underground Railroad Collection, <a>https://ohiomemory.org/digital/collection/siebert/id/28600</a>.</small></p>
  <p id="fn3"><a href="#r3">[3]</a> <small>Still, <i>The Underground Rail Road</i>; Jeremy Mennis, “Geospatial Dataset of Cities and Counties of Escape Origin as Recorded in William Still’s Records of the Underground Railroad, 1853-1861,” <i>Journal of Slavery and Data Preservation</i> 6, no. 4 (2025): 258–66, 10.14321/jsdp.6.4.0258; Jeremy Mennis, “Geospatial Dataset of Cities and Counties of Escape Origin as Recorded in William Still’s Records of the Underground Railroad, 1853-1861,” Harvard Dataverse, 2025, <a>https://doi.org/10.7910/DVN/1BLSRL</a>.</small></p>
  <p id="fn4"><a href="#r4">[4]</a> <small>Mennis, “Geospatial Dataset of Cities and Counties of Escape Origin as Recorded in William Still’s Records of the Underground Railroad, 1853-1861,” <a>https://doi.org/10.7910/DVN/1BLSRL</a>; view this map <a href="https://arcg.is/1GCHay2">here</a>.</small></p>
  <p id="fn5"><a href="#r5">[5]</a> <small>Foner, <i>Gateway to Freedom</i>, 94–108.</small></p>
  <p id="fn6"><a href="#r6">[6]</a> <small>Sydney Howard Gay Portrait, ca. 1850-1888, photograph, Massachusetts Historical Society, Portraits of American Abolitionists, Photo. Coll. 81, Massachusetts Historical Society Photo Archives, Columbia University Libraries Online Exhibitions, <a>https://exhibitions.library.columbia.edu/exhibits/show/fugitives/item/9148</a>.</small></p>
  <p id="fn7"><a href="#r7">[7]</a> <small>Eric Foner has undertaken the most thorough and illuminating study of Gay’s work, including an overview of the Record of Fugitives; Foner, <i>Gateway to Freedom</i>, 193-210.</small></p>
  <p id="fn8"><a href="#r8">[8]</a> <small>Mennis, “Geospatial Dataset of Cities and Counties of Escape Origin as Recorded in William Still’s Records of the Underground Railroad, 1853-1861,” <a>https://doi.org/10.7910/DVN/1BLSRL</a>.</small></p>
  <p id="fn9"><a href="#r9">[9]</a> <small>Sidney Howard Gay, Record of Fugitives, 1855-1856, Columbia University Rare Book & Manuscript Library, 9-10, <a>https://exhibitions.library.columbia.edu/exhibits/show/fugitives/record_fugitives/book1/page9</a>; Still, <i>The Underground Rail Road</i>, 291.</small></p>
  <p id="fn10"><a href="#r10">[10]</a> <small>Gay, Record of Fugitives, 9-10, <a>https://exhibitions.library.columbia.edu/exhibits/show/fugitives/record_fugitives/book1/page12</a>.</small></p>
  <p id="fn11"><a href="#r11">[11]</a> <small>Gay, Record of Fugitives, 14, <a>https://exhibitions.library.columbia.edu/exhibits/show/fugitives/record_fugitives/book1/page14</a>; in instances like this when days of the week are relevant, I have used <a href="https://www.arc.id.au/Calendar.html">this historical calendar tool</a>to look them up.</small></p>
</section>

# Annotations

Demo showing a potential application of annotations using IIIF and Mirador to Open Collections.

## [Epigraphic Squeezes - Decretum de Minervae Victoriae Sacerdote Temploque (I)](https://dx.doi.org/10.14288/1.0050935)

![mirador_epigraphic.gif](https://github.com/carolamigo/ubc_mirador_epigraphic/blob/master/mirador_epigraphic.gif)

### How to do it:

- Install Mirador viewer following the instructions here: https://github.com/ProjectMirador/mirador

- Set up a local web server using Node, following the instructions here:
http://ronallo.com/iiif-workshop/preparation/web-server.html

- Run the server on the terminal by going to directory where it is installed and entering:

`http-server -p 3000 --cors`

- Get the manifest for the item to be annotated by going to the item page in Open Collection and clicking on the IIIF manifest link in the “embed” tab:

http://iiif.library.ubc.ca/presentation/cdm.squeezes.1-0050935/manifest

- Save the manifest as a JSON file in the folder where Mirador and the web server is running. Open the JSON file using a text editor such as Sublime or Atom. Replace everything on line 351 and below for this code (check [epigraphic_manifest_edited.json](https://github.com/carolamigo/ubc_mirador_epigraphic/blob/master/epigraphic_manifest_edited.json) for complete json file edited):

`
              "on": "https://iiif.library.ubc.ca/cdm.squeezes.1-0050935/canvas/p0"
            }
          ],
          "otherContent": [
            {
              "@id": "http://localhost:3000/annotation_list.json",
              "@type": "sc:AnnotationList",
              "label": "Text of this page"
            }
          ]
        }
      ]
    }
  ],
  "description": "[No description]",
  "@context": "http://iiif.io/api/presentation/2/context.json",
  "@id": "http://localhost:3000/epigraphic_manifest_edited.json",
  "@type": "sc:Manifest"
}
`

- By using a text editor such as Sublime or Atom, create an HTML file named “epigraphic.html”. Paste in the code available at [epigraphic.html](https://github.com/carolamigo/ubc_mirador_epigraphic/blob/master/epigraphic.html).

- Open “epigraphic.html” on your browser. Click on “add item”, open the item, and toggl annotations on (button on the left upper corner). Draw your annotations on your image using this feature of Mirador.

- The annotations will be stored in the local cache of your browser until it is closed. We need to retrieve the annotations from the local cache. In Firefox, on the Mirador window with the annotations, go to Tools > Web Developer > Inspector > Storage tab > Local storage. Select the value line and then the data line on the right. Copy and paste the data on a text editor such as Sublime or Atom, saving it as a JSON file named “annotation_list.json”. Remove the URL at the beginning of the code, the double quotes and square brackets (from beginning and end), as the code has to start at `{“@context (...)`. A version of the final annotation code, easier to read, is available at [annotation_list.json](https://github.com/carolamigo/ubc_mirador_epigraphic/blob/master/annotation_list.json) for reference.

![epigraphic_localstore.png](https://github.com/carolamigo/ubc_mirador_epigraphic/blob/master/epigraphic_localstorage.png)

- Open the epigraphic.html file on your browser to see the final result. Click on Add item to see the menu with options.

## References

References:

- http://ronallo.com/iiif-workshop/presentation/image-annotation.html
- http://iiif.io/api/presentation/2.1/#image-resources
- http://darthcrimson.org/hacking-mirador/
- http://www.darthcrimson.org/hacking-mirador-workshop/annotate.html


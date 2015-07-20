# MuseParse
Repository for a python music parser. This works with MusicXML as the input format which forms a tree of objects in memory representing the piece. This can be optionally outputted to lilypond which produces a PDF, or perused for your own uses. All classes are intentionally loosely coupled, so if you would like to put in another input or output format as may come later, please do suggest them in issues and if you want, work on it yourself. For now, MusicXML is a fairly standard format. 

Written for python 3 only, python 2.7 support may come later but I'm not intending on doing that unless everything else is done.

Originally written as part of my Final Year Project (or dissertation project) at university. I earned 93% on this along with an application of this section so you'd hope it was good.

# Installation
I'm hoping to put this on pypi, but at the minute all you need to do until then is run the usual setup commands:
``` 
python3 setup.py build
python3 setup.py install
```

# Usage
## Parsing music
You can parse music from an xml file using the following code:
```
from MuseParse.classes.Input import MxmlParser
parser = MxmlParser.MxmlParser()
object_hierarchy = parser.parse(filename)
```
This will return a hierarchy of objects - please view the wiki for more information on the objects in this hierarchy.

## Outputting to PDF
To send it to lilypond:
```
from MuseParse.classes.Output import LilypondOutput
render_obj = LilypondOutput.LilypondRenderer(object_hierarchy, filename)
render_obj.run()
```
To provide the lilypond runner class with your own lilypond script (see http://lilypond.org installation page for more information on this):
```
from MuseParse.classes.Output import LilypondOutput
render_obj = LilypondOutput.LilypondRenderer(object_hierarchy, filename, lyscript="path/to/script")
render_obj.run()
```
Demo scripts are located in MuseParse/demo


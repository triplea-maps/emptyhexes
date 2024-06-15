empty hexes modding resource  v1.0
Created by Killgore85 with a considerable assist by Wisconsin.

This is NOT a complete mod.  In the strictest sense it is, but it's pretty lame as a mod.  The intention of this is to be a basis for other mods that use hex maps.

As it stands right now, it loads correctly in tripleA but not TripleA Map Creator v1.0.1.1 
Wisconsin tells me that the next version of Map Creator should be able to work with it.  He is also working on some other things to make it even more effectively usable.  For instance a coordinate shifter (he already made the great Map Resizer).  I was originally creating this at 3 sizes, but with the resizer, it's much more effective to just do it at 1 size and then let the user resize it to the size desired.

I am working on a full 100x100 hex map modding resource and in fact I am most of the way through it.  Much of that work is included in this release.  All that is left is to finish the centers, polygons, and place files.  When Wisconsin is done with his coordinate shifter, I'll finish that off since it will be vastly easier and less time consuming using that than doing it manually.  If anyone is curious, I'm going to do it by making copies of what's done, shifting the coordinates, renaming the shifted locations, then adding them to the original ones.

The map.properties and place files are done with the unit size at 50% because the hexes are too small to effectively see what's going on in most games.  The size IS excellent for testing and is much better for manipulating since the memory requirements aren't as steep.  When you are otherwise done with your mod, just use Wisconsin's Map Resizer to resize it to 200% and change the unit size in the map.properties file to 100% and you will have a very usable size for most mods.  You can of course make it bigger to allow more units, but you will also need to redo the place file then.  It's very easy to do that in part one of the map creator using the auto-placement finder but it may take a while for the program to run (skip step 5, and go right to step 6).

I have all the hexes set as land hexes in the mod's xml file.  If you want to use mostly water/space areas I have included the file "territory names- water 65x20.txt" which you can copy the contents of and just replace the existing territory names with those.  

Presumably you will want to use a different size hex map, for instance 20x20 hexes instead of 65x20.
I have done what I can to make it easier to modify what I've done.  Specifically, I arranged each hex's name in order and made them start on their own line with a blank line seperating each column of hexes (example 0101, 0102...0100 is one column). In the case of the polygons file, Ihave a blank line sperating each hax.  

In the mod's xml file for the connections, each hex has 3 primary connections (t1) and 3 secondary connections (t2).  All of the connections are listed in order numerically with all three primary connections on one line (you can't do both in order at the same time).  The connections were created with the primary connections always connecting to the left and up.  Doing it this way allows you to delete a line of 3 connections and the lines below it (in the same column) to eliminate any reference to those hexes.  Obviously deleting all the connections for an unused column will also be easy.  Then all you need to do is remove any left over connections to hexes that no exist.  Doing that can be done 1 of 2 ways.  
	1) easy: Either remove the last column's connections + the last hex in each column's connections then save the file and load it into map creator part 2 and use the auto connection finder to fill in the missing connections.
	2) harder but better organized and easier to modify later: manually edit the xml file by removing or commenting out any references to unused hexes.  Be warned that even columns and odd columns don't connect in the same way, neither does the very first column. In the xml that I have provided, I have commented the unused hexes out for better organization.

For organization, I've put the each hex's attatchments on one line with a comment at the end of the line reminding you which hex it is since the lines are too long to see all at once.

I haven't included either the baseTiles or reliefTiles folders since they are very easy to create once you have edited the map to the size you want with map creator.  In addition, you'd need to recreate them anyway unless you use exactly the same sized map that I have provided.  

You'll almost certainly want to work from the map pics that include hex numbers, because it's much easier to see what's going on.

Lastly, This is resource is one of two different different ways that hex maps are generally designed.  The other way is 0101 attatching to 0201's bottom left side instead of it's top left and expanding the map from there.  The other way can easily be created based on editing what I've done but it's probably more work than it's worth and I don't intend to do it myself.  The same thing applies to the naming convention of starting the numbers at 0000 or 0001 instead of 0101.  If someone else wants to, by all means feel free, just give me credit for the work I've done.

Here's a checklist what you will need to do to modify the map:
	1) edit the maps picture to the size (number of hexes) that you want by trimming off the excess hexes. 
	2) edit the map.properties file to reflect the new map's dimensions.
	3) create new base tiles with part 1 of map creator.
	4) create a new smallMap.jpeg (it MUST be named EXACTLY that, smallMap.jpg isn't good enough)
	5) edit the centers file by removing any unused hexes.
	6) edit the polygons file by removing any unused hexes.
	7) edit the place file by removing any unused hexes.
	8) edit the mod's xml file by removing any unused hexes.
	9) use the map resizer to scale it to the size you want.
	10) edit the map.properties file by setting the unit size to 100% (presumably you'll want this setting at 100% for better visibility)

==============================================

A couple of notes when creating mods:

Some things WILL work with tripleA but not map creator.  For example:
	1) Having spaces in names (you can use them in both but they won't transfer correctly from the centers file created in part 1 of map creator so they may need to be retyped in every time that name should pop up).  If you really want spaces, you can use a stand in character like _ when you use map creator, then edit the files with notepad and replace _ with space.
	This may or may not apply to having periods or dashes in names also, I haven't checked that out.

	2) If you modify the xml directly, and you use the tab button (with notepad for example) it may cause errors in either, but it's much more likely in map creator.  The only significant reason to use them is for organization, to see what's going on with the xml file more easily.
	For example, the second one causes an error in map creator but both work with tripleA.
   <playerProduction player="xxxx" frontier="production"/>
   <playerProduction player="xxxx"	frontier="production"/>
	Another example of that problem is with tech attachments.

	3) If you modify the xml directly, make sure you save the file as the correct file type.  Notepad will automatically save the file as either a txt file (if you use "save as") or else it will replace the existing file as the opened/current type if you use "save".  
	You CAN tell it to save as a different file type using "save as" but you need to have the "." then the file type at the end of the file name and you also have to select "All Files" in the "Save as Type:" box.

	4) It's vastly easier to find out what is causing a bug if you work making small changes, then check your work.  It may well go faster also, since the memory requirements aren't as steep.

	5) Some things are much easier to do with map creator than editing any of the game files directly, some are much harder.  In particular, a lot of the repetetive work is much easier modifying the file directly.
	Particularly with larger files, it may be easier (it will definitely be quicker if you are editing something big) working on a small section of the project and then adding it to the larger whole.
	6) If you're working with a larger map, you may find it to be easier and less (probably much less) time consuming to create it at half scale and define the unit size (in the initial step of part 1 of map creator) as 50%.  
	Then use the new TripleA Map Image Extractor (it comes with TripleA Map Creator v1.0.1.1 and later versions as a seperate file) to expand it to 100% when you are done.  All the files (including the placement file) should then be correct at the 100% size.  The only file that you'll probably wan't to edit after that is the map.properties file, setting the unit size to 100%.
	Another advantage of doing the mod this way is that you can create bigger maps because the memory requirements aren't as severe.

	7) Personally, I've had quite a few problems with malformed bytes sneaking into my work.  Google it for a description.  At one point, I was incorrectly referring to them as bleed characters.  They can cause any number of different errors that can be really tough to track down.  If anyone knows of a good program for this, I'd really appreciate knowing about it since they don't show up as visibly obvious characters in notepad, wordpad or word. 
	Here's an example of what I'm talking about: "> 
3303"
	I copied that example from notepad, where it showed everything between the "" on one line with no visibly obvious character.  If you advanced the cursor using an arrow key it WOULD show up, appearing by requiring you to hit the arrow key twice to get to the next visible character.  If you check out the txt file below you'll see what I mean.

	8) working with map creator, the map itself can have any number of colors, even within the same territory, the only restrictions
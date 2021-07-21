# Talking Electronics Micro Computer

Project is incomplete....If you are here please come back later.  Will be finished by Mid August 2021

Welcome to the Talking Electronics Microcomp project page.  If you are interested in building the Microcomp head to the [Project](./project) folder.  If you would like to read the original documentation then look in the [Documents](./documents) folder, and if you would like to know a bit of its history keep reading.

The [Talking Electronics](http://www.talkingelectronics.com/te_interactive_index.html) Micro Computer or Microcomp for short was a 3-Chip Computer based on the Z80 Microprocessor.  It was created in the Mid 80's by Colin Mitchell the founder of TE and sold as a single board microcontroller.  Its purpose was as a Z80 trainer to compete/complement with the Talking Electronic Computer (TEC) and be used to control and automate various external devices like lights, sensors and relays.  But realistically due to its large size, lack of memory and lack of expansion the product never sold well.

The Microcomp had a number of things that went against being a viable product.
*  It was hard to program.  It was built with one 4k 2732 EPROM.  There was no way to modify code directly on the board.  The EPROM needed to be removed and placed in a EPROM burner of some sort.  This took time and trying to debug the code took a lot of time.
*  It had no RAM.  This hugely limits the use of the Microcomp.  Not only the code had to be written without stack manipulation op codes, but productive programs just can't be made.  This was obvious quite early on as almost all 'Add Ons' had the inclusion of on board RAM.  This then turned the 3-Chip computer into a 4+ chip something totally different and something that isn't unique.
*  It has no useable input device or output screen.  Having a DIP switch to input data is okay for set-and-forget, but it's supposed to be a Z80 trainer.  Only two button's were provided with the extension of two more.  Having only 2 seven segments to display data is also very limiting.  A program was made on the initial EPROM to read memory and output it.  It was quite clever in operation, but tedious to use.
*  Technology was changing rapidly at the time.  The Z80 CPU is a large chip with 40 pins.  It was being phased out with smaller microprocessors in particularly the PIC microcontrollers.  Colin also saw this and moved a lot of his microprocessing hardware to use PIC controllers.
*  Talking Electronics Computer - The TEC was released by Talking Electronics a few years prior to the Microcomp.  The TEC is far more superior to the Microcomp.  It was a single board computer with hex keyboard, full address and data output to 6 seven segment displays, ROM/RAM and it was expandable.  Why would you need a Microcomp when you can get a TEC to do the same, plus much more.  It is recommended in the Microcomp publication to use the TEC to program the Microcomp!  The creators of the TEC (John,Ken) have negative feelings towards the Microcomp as they feel it was created by Colin due to their product being much better than what Colin could do.

Though the Microcomp was a bit limiting, it did have some interesting design options due to the fact that it was only built with 3 chips.  Having no memory selection chip (typically a 74LS138), clever transistor logic was implemented using the a combination of the IORQ line with A0 and A1.  For instance, when a `IN A,(01)` is sent to the CPU, IORQ goes low and A0 goes high, this activates the input latch transistor and the high signal from A0 feeds into the DIP switch, which then sets bits on the Data Bus. Then finally the data on the Data Bus read by the CPU and store in register A.  A similar circuit is used to activate the output latch for the seven segments.

Having two seven segments had a challenge as to which segment would be active when data was sent to it.  Bit 7 on the Data Bus was used to switch between the two segments.  Again using transistor logic, a high on D7 would activate the left hand segment and deactivate the right hand segment.  And the opposite applies when D7 is low.  The decimal point on the seven segments was sacrificed for this feature to work.

From a programming perspective, Z80 coding without RAM is a challenge.  I think it's a good challenge.  Only having limited storage on the CPU itself makes the programmer think differently on how to do a particular task.  Code has to be much more structured, registers need to have a defined purpose.  The Master Mind game on the upper ROM, is something that I converted to be RAM-less.  I had to be very careful in how I used the CPU registers.  It was a good but sometimes frustrating time writing it.

## Why did I do this project!!
Like with all Retro computing, if you want something quicker, smaller, better get a modern device.  I recently got into the Retro computer scene and Talking Electronic was an influence to my interest in Electronics.  The publications that Colin wrote are still today helpful in learning Electronics.

In the late 80's I was fortunate to build a TEC, it was a fantastic project for me.  I also was into coding.  I probably became a software engineer because of it.  The Microcomp was also something that intrigued me.  As there were no original boards to purchase, I designed my own board and after about a year of it sitting around, I finally built it.  I felt I needed to preserve the project, so I fully [annotated](./documents/microcomp_lower_rom_listing.pdf) the original 2k ROM and compiled all references to it.

There is some interest in the Microcomp from the TEC community.  I decided to rework the PCB as the prototype that I created had issues.  I got personal approval from Colin to advance the project and make it the next version of the Microcomp.  I'm also aware that some of the original people involved with TE who were *hard done* by Colin at the time feel negative towards the Microcomp.  Though from my perspective, as I wasn't emotionally involved in its creation, I would like to give others the chance to build one if they would like to.  That is what modern day Retro Computing is all about.

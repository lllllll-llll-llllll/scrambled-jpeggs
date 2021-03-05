project idea:
      simple cli tool to scramble or unscramble an image
  
possible cli usage:
    scrambling:
        scrambled-jpeggs --scramble -i <input>
        scrambled-jpeggs --scramble -i <input> -o <output>
        scrambled-jpeggs --scramble -i <input> -o <output> -w 6 -h 10
        
    solving:
        scrambled-jpeggs --unscramble -i <input>
        scrambled-jpeggs --unscramble -i <input> -o <output>

possible flags:
    -s --scramble : mode to scramble image
    -u --unscramble : mode to unscramble image
    -i --input : input file
    -o --output : output file
    -w --width : number of vertical columns that image is scrambled by
    -h --height : number of horizontal rows that image is scrambled by
    
        
operation:
    scrambling: 
        - divide the image into a grid of small rectangles
        - randomly reassemble the image, but keep the topleftmost in place
        - grid dimensions by default are based on image dimensions
          but can be specified with -x <width> -y <height>
        - use imagemagick
        
    unscrambling:
        - analyze hough's lines to detect grid dimsions for scrambled image
        - divide the image up into small rectangles according to that grid
        - top left rectangle remains unscrambled so we use that as our start
        - compare each rectangle to find a matching edge that is most similar
        - use imagemagick
        






























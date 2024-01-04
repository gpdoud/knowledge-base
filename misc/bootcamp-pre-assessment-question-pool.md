* Reasoning

    All salespersons are rich
    Jane is rich
    Therefore Jane is a salesperson
    true/(false)/uncertain

        All teachers are educated
        Jim is educated
        Therefore Jim is a teacher
        true/(false)/uncertain

        All welders are skilled
        Karen is skilled
        Therefore Karen is a welder
        true/(false)/uncertain

        All fire fighters are brave
        Joe is brave
        Therefore, Joe is a fire fighter
        true/(false)/uncertain

        All softball players are athletes
        Michelle is an athlete
        Therefore, Michelle is a softball player
        true/(false)/uncertain

    All dogs are canines
    Fido is a dog
    Therefore Fido is a canine
    (true)/false/uncertain

        All women are rational
        Jane is a woman
        Therefore Jane is rational
        (true)/false/uncertain

        All police officers are in law enforcement
        Cathy is a police officer
        Therefore Cathy is in lay enforcement
        (true)/false/uncertain

        All CEOs make a lot of money
        Denise is a CEO
        Therefore Denise makes a lot of money
        (true)/false/uncertain

        All cats are felines
        Felix is a cat
        Therefore Felix is a feline
        (true)/false/uncertain

    All motorcycles are vehicles
    Some vehicles are electric
    Therefore all motorcycles are electric
    true/false/(uncertain)

        All sedans are cars
        Some cars are electric
        Therefore all sedans are electric
        true/false/(uncertain)

        All A are B
        Some B are C
        Therefore all A are C
        true/false/(uncertain)

    Some workers are not contractors
    Some contractors are expensive
    Therefore some workers are expensive
    true/(false)/uncertain

    All Coke is soda
    Some Coke is sugar-free
    Therefore some soda is sugar-free
    (true)/false/uncertain
    
* Logic

    if x = y, and y = z
    then x = z (true) x=1, y=1, z=1

    if x > y, and z > y
    then x = z (false) x=1, y=0, z=2

    if x <= y and y <= z
    then x < z (false) x=0, y=0, z=0

    if x not > y and y not > z
    then x <= z (true) x=1, y=1, z=1

    if y > x and z < y
    then x not < z (false) x=1, y=3, z=2

* Math

    if y = 3x - 2, calulate y if x = 4 (y = 10)
    if y = 2x - 1, calulate y if x = 3 (y = 5)
    if y = 4x + 9, calulate y if x = 5 (y = 29)
    if y = 7x - 5, calulate y if x = 2 (y = 9)
    if y = 5x + 3, calulate y if x = 7 (y = 38)

    if y =  5x^2 + 9x + 3, calculate y if x = 7 (y = 311)
    if y = -3x^2 + 8x - 2, calculate y if x = 7 (y = -93)
    if y =  6x^2 - 2x + 8, calculate y if x = 3 (y = 56)
    if y = -8x^2 + 7x + 4, calculate y if x = 3 (y = -47)
    if y = 13x^2 - 3x - 3, calculate y if x = 2 (y = 43)

    if y = 2.5x + 1.9, calculate y if x = 2.5 (y = 8.15)
    if y = 8.7x + 9, calculate y if   x = 1.8 (y = 24.66)
    if y = 5.6x + 7.8, calculate y if x = 4.5 (y = 33)
    if y = 7.5x + 2.4, calculate y if x = 5.2 (y = 41.4)
    if y = 5x   + 8, calculate y if   x = 6.5 (y = 40.5)

    if y = (x^2 + 4)^2, calculate x if x = 2  (y = 64)
    if y = (x^3 + 1)^2, calculate x if x = -3 (y = 676)
    if y = (x^4 + 2)^2, calculate x if x = -2 (y = 324)
    if y = (x^6 + 8)^2, calculate x if x = 1  (y = 81)
    if y = (x^3 + 3)^2, calculate x if x = 2  (y = 121)

    if y = x^2 + 9x + 20, calculate BOTH values for x if y = 0 (x = -4 || x = -5)
    if y = x^2 + 3x - 18, calculate BOTH values for x if y = 0 (x = 3 || x = -6)
    if y = x^2 - 6x + 8, calculate BOTH values for x if y = 0 (x = 4 || x = 2)
    if y = x^2 + 10x + 21, calculate BOTH values for x if y = 0 (x = -3 || x = -7)
    if y = x^2 + 2x - 63, calculate BOTH values for x if y = 0 (x = 7 || x = -9)

* Programming

    You must create a code for each clothing product based on these rules:
    Gender (chars 1-2)
        00 - for either male or female clothing
        01 - for female clothing
        02 - for male clothing
    Size (chars 3-4)
        PT - petite
        SM - small 
        MD - medium
        LG - large
    Material (chars 5)
        C - cotton
        P - Polyester
        W - wool
        B - cotton/polyester blend
        S - silk
    Price (chars 6-10) no decimal point needed
        dollars (chars 6-8) leading zeros ($9 = 009, $12 = 012)
        cents (chars 9-10)
    Product is on sale (char 11)
        no character - regular price (not discounted or clearance priced)
        D - discounted price
        C - clearance price
    Example: A cotton dress in size small. regular price $23.98: 01SMC02398

    A men's wool jacket, size large, regular price $435.99. (02LGW43599)
    A men's cotton jacket, size medium, clearance price $234.98. (02MDC23498C)
    A men's wool jacket, size small, discounted price $535.97. (02SMW53597D)
    A men's polyester jacket, size medium, regular price $335.96. (02MDP33596)
    A men's blend jacket, size large, regular price $485.95. (02LGB48595)

    A woman's blend pants, regular price of $45.88, in size medium (01MDB04588)
    A woman's silk pants, discounted to $55.88, in size petit (01PTS05588D)
    A woman's cotton pants, regular price of $35.87, in size small (01SMC03587)
    A woman's wool pants, clearance price of $27.98, in size large (01LGW02798C)
    A woman's polyester pants, regular price of $395.48, in size medium (01MDP03948)

    A size small, polyester sports shirt for women or men, clearance price at $9.66 (00SMP00966C)
    A size large, blend sports shirt for women or men, regular price at $12.62      (00LGP01262)
    A size medium, wool sports shirt for women or men, regular price at $23.56      (00MDP02356)
    A size petit, cotton sports shirt for women or men, discounted price at $17.73  (00PTP01773D)
    A size petit, silk sports shirt for women or men, regular price at $33.21       (00PTP03321)

    A woman's petite, silk, evening gown, regular price at $1285.42.        (01PTS28542)
    A woman's medium, wool, evening gown, discounted price at $563.82.      (01MDW56382D)
    A woman's large, cotton, evening gown, clearance price at $453.43.      (01LGC54343C)
    A woman's petite, polyester, evening gown, regular price at $375.24.    (01PTP37524)
    A woman's small, blend, evening gown, discounted price at $244.88.      (01SMB24488D)

    A medium size wool hat for men or women,        regular price at $152.47.    (00MDW15277)
    A small size cotton hat for men or women,       discounted price at $92.62.  (00SMC09262D)
    A medium size polyester hat for men or women,   clearance price at $72.24.   (00MDP07224C)
    A large size blend hat for men or women,        regular price at $52.41.     (00LGB05241)
    A small size wool hat for men or women,         discounted price at $132.93. (00SMW13293D)

* Series

    Determine the next number in the series.

    (add 1, add 2, add 3, ...)
    1, 2, 4, 7, 11, ? (16)
    6, 7, 9, 12, 16, ? (21)
    3, 4, 6, 9, 13, ? (18)
    12, 13, 15, 18, 22, ? (27)
    44, 45, 47, 50, 54, ? (59)

    (2x3, 2x6, 2x12, ...)
    3, 6, 12, 24, 48, ? (96)
    2, 4, 8, 16, 32, ? (64)
    4, 8, 16, 32, 64, ? (128)
    5, 10, 20, 40, 80, ? (160)
    7, 14, 28, 56, 112, ? (224)

    (-2x)
    2, -4, 8, -16, 32, ? (-64)
    3, -6, 12, -24, 48, ? (-96)
    4, -8, 16, -32, 64, ? (-128)
    5, -10, 20, -40, 80, ? (-160)
    7, -14, 28, -56, 112, ? (-224)

    (prev * 3 + 1)
    1, 4, 13, 40, 121, ? (364)
    2, 7, 22, 67, 202, ? (607)
    3, 10, 31, 93, 280, ? (841)
    4, 13, 40, 121, 364, ? (1093)
    5, 16, 49, 148, 445, ? (1336)

    (prev - 1 * 2)
    3, 4, 6, 10, 18, ? (35)
    4, 9, 16, 30, 58, ? (114)
    5, 8, 14, 26, 50, ? (98)
    7, 12, 22, 42, 82, ? (162)
    6, 10, 18, 34, 66, ? (130)

    (prev - 3 * -3)
    2, 3, 0, 9, -18, ? (45)
    4, -3, 18, -45, 135, ? (-396)
    5, -6, 27, -72, 225, ? (-666)
    7, -12, 45, -126, 378, ? (-1125)
    9, -18, 63, -180, 549, ? (-1638)

    (rotate digits)
    5247, 2475, 4752, 7524, 5247, 2475, ? (4752) 
    7439, 4397, 3974, 9743, 7439, 4397, ? (3974)
    4936, 9364, 3649, 6493, 4936, 9364, ? (3649)
    1625, 6251, 2516, 5162, 1625, 6251, ? (2516)
    6847, 8476, 4768, 7684, 6847, 8476, ? (4768)

    KDJS, DKJS, DJKS, KJSK, JKSK, DKJS, ? (DJKS)
    HDSI, DHSI, DSHI, DSIH, SDIH, DHSI, ? (DSHI)
    NWIX, WNIX, WINX, WIXN, IWXN, WNIX, ? (WINX)
    IENF, EINF, ENIF, ENFI, NEFI, EINF, ? (ENIF)
    CIGB, ICGB, CGIB, CHBI, HCBI, ICGB, ? (CGIB)
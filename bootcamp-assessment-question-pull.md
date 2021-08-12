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
    Therefore some motorcycles are electric
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

    if x = y, and x = z
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

    if y = 3x -2, calulate y if x = 4 (y = 10)

    if y = -5x^2 + 6x -2, calculate y if x = 7 (y = -205)

    if y = 1/4x^2 -1/2x + 3/8, calculate y if x = 3 (y = 27/8)

    if y = sqrt(x^3 + 8), calculate x if y = 4 (x = 2)

    if y = x^2 + 9x + 20, calculate BOTH values for x if y = 0 (x = -4 || x = -5)

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

    A woman's blend pants, discounted to $45.88, in size medium (01MDB04588D)

    A size small, polyester sports shirt for women or men, clearance price $9.66 (00SMP00966C)

    A woman's petite, silk, evening gown, priced at $285.42. (01PTS28542)

    A medium size wool hat for men or women, discounted to $152.77. (00MDW15277D)

* Series

    Determine the next number in the series.

    1, 2, 4, 7, 11, ? (add 1, add 2, add 3, ...)
    6, 7, 9, 12, 16, ?
    3, 4, 6, 9, 13, ?
    12, 13, 15, 18, 22, ?
    44, 45, 47, 50, 54, ?

    3, 6, 12, 24, 48, ? (2x3, 2x6, 2x12, ...)
    2, 4, 8, 16, 32, ?
    4, 8, 16, 32, 64, ?
    5, 10, 20, 40, 80, ?
    7, 14, 28, 56, 112, ?

    2, -4, 8, -16, 32, ? (2x-2, -4x-2)
    3, -6, 12, -24, 48, ?
    4, -8, 16, -32, 64, ?
    5, -10, 20, -40, 80, ?
    7, -14, 28, -56, 112, ?

    1, 4, 13, 40, 121, ? (prev * 3 + 1)
    2, 7, 22, 67, 202, ?
    3, 10, 31, 93, 280, ?
    4, 13, 40, 121, 364, ?
    5, 16, 49, 148, 445, ?

    3, 4, 6, 10, 18, ? (prev - 1 * 2)
    4, 9, 16, 30, 58, ?
    5, 8, 14, 26, 50, ?
    7, 12, 22, 42, 82, ?
    6, 10, 18, 34, 66, ?

    2, 3, 0, 9, -18, ?  (prev - 3 * -3)
    4, -3, 18, -45, 135, ?
    5, -6, 27, -72, 225, ?
    7, -12, 45, -126, 378, ?
    9, -18, 63, -180, 549, ?

    5247, 2475, 4752, 7524, 5247, 2475, ? (rotate digits)
    7439, 4397, 3974, 9743, 7439, 4397, ?
    4936, 9364, 3649, 6493, 4936, 9364, ?
    1625, 6251, 2516, 5162, 1625, 6251, ?
    6847, 8476, 4768, 7684, 6847, 8476, ?

    KDJS, DKJS, DJKS, KJSK, JKSK, DKJS, ?
    HDSI, DHSI, DSHI, DSIH, SDIH, DHSI, ?
    NWIX, WNIX, WINX, WIXN, IWXN, WNIX, ?
    IENF, EINF, ENIF, ENFI, NEFI, EINF, ?
    CIGB, ICGB, CGIB, CHBI, HCBI, ICGB, ?
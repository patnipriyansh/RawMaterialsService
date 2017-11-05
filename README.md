# RawMaterialsService
Scanner scan = new Scanner(System.in);
        System.out.println("Enter the number of sacks");
        int numSack = scan.nextInt();
        
        int counter  = 0;
        ArrayList<Double> cement = new ArrayList<>(); 
        ArrayList<Double> gravel = new ArrayList<>();
        ArrayList<Double> sand = new ArrayList<>();
        boolean name;
        boolean under;
        boolean over;
        int rejected = 0;
        Double weightS;
        Double weight = 0.0;
        String content = "0";
        
        do {
            name = false;
            under = false;
            over = false;
            
            System.out.println("Enter the content of the sack");
            content = scan.next();
            
            System.out.println("Enter the weight of the sack");
            weight = scan.nextDouble();
            
            
            if (content.equalsIgnoreCase("cement")) {
                
                if (weight < 24.9) {
                    under = true;
                    rejected += 1;
                } else if (weight > 25.1){
                    over = true;
                    rejected += 1;
                } else {
                    counter += 1;
                    cement.add(weight);
                }
                
            } else if (content.equalsIgnoreCase("gravel")) {
                
                if (weight < 49.9) {
                    under = true;
                    rejected += 1;
                } else if (weight > 50.1){
                    over = true;
                    rejected += 1;
                } else {
                    counter += 1;
                    gravel.add(weight);
                }
                
            } else if (content.equalsIgnoreCase("sand")) {
                
                if (weight < 49.9) {
                    under = true;
                    rejected += 1;
                } else if (weight > 50.1){
                    over = true;
                    rejected += 1;
                } else {
                    counter += 1;
                    sand.add(weight);
                }
                
            } else {
                name = true;
                rejected += 1;
            }
            
            if (name == true || over == true || under == true) {
                System.out.println("The name entered is " + !name);
                System.out.println("Sack is overweight: " + over);
                System.out.println("Sack is underweight " + under);
            }
            
                       
        }while( counter <= numSack );
        
        int i;
        double sum = 0;
        
        for (i = 0; i < cement.size(); i++) {
            sum += cement.get(i);
        }
        
        for (i = 0; i < gravel.size(); i++) {
            sum += gravel.get(i);
        }
        
        for (i = 0; i < sand.size(); i++) {
            sum += sand.get(i);
        }
        
        System.out.println("Total weight is: " + sum);
        System.out.println("Total number of rejected items: " + rejected);
        
        int priceCement = 3 * cement.size();
        int priceGravel = 2 * gravel.size();
        int priceSand = 2 * sand.size();
        int regularPrice = priceSand + priceGravel + priceCement;
        
        int finaln = 0;
        int min = sand.size()/2;
        int min2 = gravel.size()/2;
        if (min <= min2) {
            finaln = min;
        } else {
            finaln = min2;
        }
        
        int discount = 0;
        
        if (cement.size() > finaln) {
            discount = 10 * finaln;
        } else {
            finaln = cement.size();
            discount = 10 * finaln;
        }
        
        System.out.println("The number of special packs: " + finaln);
        System.out.println("The regular price is: " + regularPrice);
        System.out.println("The discount value is " + discount);
        System.out.println("The final price after discount is " + (regularPrice - discount));


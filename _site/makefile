cat:
	touch njaccidents.csv
	echo "case code,County Name,Municipality Name,Crash Date,Crash Day Of Week,Crash Time,Police Dept Code,Police Department,Police Station,Total Killed,Total Injured,Pedestrians Killed,Pedestrians Injured,Severity,Intersection,Alcohol Involved,HazMat Involved,Crash Type Code,Total Vehicles Involved,Crash Location,Location Direction,Route,Route Suffix,SRI (Std Rte Identifier),MilePost,Road System,Road Character,Road Surface Type,Surface Condition,Light Condition,Environmental Condition,Road Divided By,Temporary Traffic Control Zone,Distance To Cross Street,Unit Of Measurement,Directn From Cross Street,Cross Street Name,Is Ramp,Ramp To/From Route Name,Ramp To/From Route Direction,Posted Speed,Posted Speed Cross Street,Latitude,Longitude,Cell Phone In Use Flag,Other Property Damage,Reporting Badge No." > njaccidents.csv
	num1=2008 ; while [[ $$num1 -le 2013 ]] ; do \
		((num2 = num1)) ; ((num3=num2)) ; \
		for county in "Atlantic" "Bergen" "Burlington" "Camden" "CapeMay" "Cumberland" "Essex" "Gloucester" "Hudson" "Hunterdon" "Mercer" "Middlesex" "Monmouth" "Morris" "Ocean" "Passaic" "Salem" "Somerset" "Sussex" "Union" "Warren" ; do \
			cat unzips/$${county}$${num1}Accidents.txt >> njaccidents.csv ; \
			done ;\
		((num1 = num1 + 1)) ; \
	done

unzip:
	mkdir -p unzips
	num1=2008 ; while [[ $$num1 -le 2013 ]] ; do \
		((num2 = num1)) ; ((num3=num2)) ; \
		for county in "Atlantic" "Bergen" "Burlington" "Camden" "CapeMay" "Cumberland" "Essex" "Gloucester" "Hudson" "Hunterdon" "Mercer" "Middlesex" "Monmouth" "Morris" "Ocean" "Passaic" "Salem" "Somerset" "Sussex" "Union" "Warren" ; do \
			unzip zips/$${county}$${num1}Accidents.zip -d unzips/ ; \
			done ;\
		((num1 = num1 + 1)) ; \
	done ; \
	mv "unzips/Cape May2011Accidents.txt" unzips/CapeMay2011Accidents.txt
	mv "unzips/Cape May2012Accidents.txt" unzips/CapeMay2012Accidents.txt
	mv "unzips/Cape May2013Accidents.txt" unzips/CapeMay2013Accidents.txt

dl:
	mkdir -p zips

	num1=2008 ; while [[ $$num1 -le 2013 ]] ; do \
		((num2 = num1)) ; ((num3=num2)) ; \
		for county in "Atlantic" "Bergen" "Burlington" "Camden" "CapeMay" "Cumberland" "Essex" "Gloucester" "Hudson" "Hunterdon" "Mercer" "Middlesex" "Monmouth" "Morris" "Ocean" "Passaic" "Salem" "Somerset" "Sussex" "Union" "Warren" ; do \
			curl -o zips/$${county}$${num1}Accidents.zip http://www.state.nj.us/transportation/refdata/accident/$${num2}/$${county}$${num2}Accidents.zip; \
			done ;\
		((num1 = num1 + 1)) ; \
	done
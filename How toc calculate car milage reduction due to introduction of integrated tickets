#integrated Ticket Approach 
print(total_distance)
large_urban=[]
urban=[]
rural=[]

commute_car=((df['TripPurpose_B01ID'] == 1) & (df['MainMode_B04ID']==3))
travel_services=((df['MainMode_B04ID']== 3) & ((df['TripPurpose_B01ID'] == 3) | (df['TripPurpose_B01ID'] == 4) | (df['TripPurpose_B01ID'] == 6)))
travel_social=((df['MainMode_B04ID']== 3) & ((df['TripPurpose_B01ID'] == 5) | (df['TripPurpose_B01ID'] == 7) | (df['TripPurpose_B01ID'] == 8) | (df['TripPurpose_B01ID'] == 9) | (df['TripPurpose_B01ID'] == 10) | (df['TripPurpose_B01ID'] == 11)))

reason_travel=commute_car | travel_services | travel_social

large_urban= df1[df1['Settlement2011EW_B04ID']==1]['HouseholdID'].tolist()
urban = df1[df1['Settlement2011EW_B04ID']==2]['HouseholdID'].tolist()
rural= df1[df1['Settlement2011EW_B04ID']==3]['HouseholdID'].tolist()

large_urban_car=df[(df['HouseholdID'].isin(large_urban))& reason_travel]
large_urban_distance=large_urban_car['TripDisExSW'].sum()
print(large_urban_distance)
urban_car=df[(df['HouseholdID'].isin(urban))& reason_travel]
urban_distance=urban_car['TripDisExSW'].sum()
print(urban_distance)
rural_car=df[(df['HouseholdID'].isin(rural))& reason_travel]
rural_distance=rural_car['TripDisExSW'].sum()
print(rural_distance)

intticket_largeurban=large_urban_car.sample(frac=0.82, random_state=42)
intticket_largeurban_dis=intticket_largeurban['TripDisExSW'].sum()
print('distance of intticket trips in large urban areas', intticket_largeurban_dis)

intticket_urban=urban_car.sample(frac=0.77, random_state=42)
intticket_urban_dis=intticket_urban['TripDisExSW'].sum()
print('distance of intticket trips in urban areas', intticket_urban_dis)

intticket_rural=rural_car.sample(frac=0.59, random_state=42)
intticket_rural_dis=intticket_rural['TripDisExSW'].sum()
print('distance of intticket trips in rural areas', intticket_rural_dis)

total_reduced_dis=intticket_largeurban_dis+intticket_urban_dis+intticket_rural_dis
reduction_perc=(total_reduced_dis/total_distance)*100
print('reductuion percentage from total distance is due to integrated ticket use',reduction_perc)

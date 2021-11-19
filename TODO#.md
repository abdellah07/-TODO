# Commandes
      - sqlite3 /gctmp/anaji/working_dir/amr/data/ezt/mer_param_pack.db
      - INSERT INTO "MER_AIRLINES_PARAMETERS" VALUES(NULL,NULL,'blabla','Y','AIR_DISCOUNT_SUBSCRIBER','AC','AMR');



# TODO 

### MAIN task --> SEATMAP into MERCTQ
      - Model --> Facade 
### SeatMap to AMR6
  - BomToPhysicalSeatmapQuery :heavy_check_mark:
  - PhysicalSeatmapResponseToBom :heavy_check_mark:
  - Seatmap :heavy_check_mark:
  - SeatmapsForRequest :heavy_check_mark:
  - ParallelPhysicalSeatmapService :heavy_check_mark:
  - SinglePhysicalSeatmapService :heavy_check_mark:
  - SeatMapQuotaRetrieverImpl :heavy_check_mark:
  - SeatProductsToBomMapper --> add  retrieveSeatProductsForSeatmap :heavy_check_mark:
  - Creation of SegmentPropertiesFacade :heavy_check_mark:


## Working On Tests
  - add The seat map to the MERCTQ service and lunch the non regression tests
  - migrate tests from rulesEvaluation to usecase AMR6 





## test Discound deleted
      - testRetrieveSeatQuotasDiscount
![first case](https://user-images.githubusercontent.com/71391891/139441447-f67d3278-b6b9-4389-a3fd-a6bb1afd6d68.png)
![image](https://user-images.githubusercontent.com/71391891/139859313-6885a064-18d7-4a19-8128-ac33857d5d82.png)
![image](https://user-images.githubusercontent.com/71391891/140046149-b6bdb6c9-7bc9-460b-9949-f2c102242d45.png)
![image](https://user-images.githubusercontent.com/71391891/140085297-7390e186-689c-485d-97f6-607ef43003f8.png)
![image](https://user-images.githubusercontent.com/71391891/142424605-087cee61-c8fd-4f67-adc4-2b6e8e695f17.png)





## what was fixed
- done : Fixing unit test in MERCTQ that where due to miss understanding of Pack and seat also due to façade constructors that needs protobuf to create the instance.

- done :  on filtring Exempted services (an exempted service is a service with packseats and only exempted segment properties) and that service should not be highlited it should be filtred
- done : building the output to be the same as expected

- change attribute of InvitoryServiceFacade to optionals to control the information needed as an output and fix the failling unit and non reg tests that came from that change

##   1 - Learn MORE about JENKINS 

## JAVA 8 --> JAVA 11
      - Jigsaw, le système modulaire
      - Méthodes privées dans les interfaces




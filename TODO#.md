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
![image](https://user-images.githubusercontent.com/71391891/139859313-6885a064-18d7-4a19-8128-ac33857d5d82.png)
![image](https://user-images.githubusercontent.com/71391891/140046149-b6bdb6c9-7bc9-460b-9949-f2c102242d45.png)





## Cases where the seatmap isn't called


##   1 - Learn MORE about JENKINS 


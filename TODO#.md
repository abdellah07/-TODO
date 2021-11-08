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





## Cases where the seatmap isn't called


##   1 - Learn MORE about JENKINS 

## JAVA 8 --> JAVA 11
      - Jigsaw, le système modulaire
      - Méthodes privées dans les interfaces
      - 
      ![image](https://user-images.githubusercontent.com/71391891/140715445-9185fda7-bef4-4688-8b7d-50263fc4ac80.png)
      - // L map.of Peut prendre jusqu'à dix entrées. Instanciation de collections immuables thoes lists are immutable.
      ![image](https://user-images.githubusercontent.com/71391891/140715660-f1950cf8-70a6-4256-a9da-80ab04d24be5.png)
      ![image](https://user-images.githubusercontent.com/71391891/140717108-ff06bdca-3014-481c-ba5a-fa0d64bc2e8a.png)
      ![image](https://user-images.githubusercontent.com/71391891/140718266-d4cec8df-1125-447a-9fd1-43499c0c819a.png)





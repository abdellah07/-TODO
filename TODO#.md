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
![secondcase](https://user-images.githubusercontent.com/71391891/139441511-81346022-1f6f-4136-8c6c-25523c1f1bcd.png)
![secondcase](https://user-images.githubusercontent.com/71391891/139441616-817dd57e-f7a0-42f4-a1b4-307b123ff0b7.png)

## Cases where the seatmap isn't called

##   1 - Learn MORE about JENKINS 


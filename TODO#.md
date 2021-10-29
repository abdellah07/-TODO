# Commandes
sqlite3 /gctmp/schenevotot/working_dir/amr/data/ezt/mer_param_pack.db
INSERT INTO "MER_AIRLINES_PARAMETERS" VALUES(NULL,NULL,'blabla','Y','AIR_DISCOUNT_SUBSCRIBER','AC','AMR');



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



##   1 - Learn MORE about JENKINS 


|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3.evbrestcontrollers"></a>EVBRestControllers

<a name="AEN90559"></a>## Name

EVBRestControllers, EVBInputStatsController, EVBQueueStatsController, EVBBarrierStatsController, EVBCompleteBarrierController, EVBIncompleteBarrierController, EVBDataLateController, EVBOutOfOrderController, EVBConnectionController, EVBFlowController -- Controllers for MVC Event Builder Statistics Packages

<a name="AEN90571"></a>## Synopsis

```
package require EVBRestControllers

EVBInputStatsController name ?option value ...?
EVBQueueStatsController name ?option value ...?
EVBBarrierStatsController name ?option  value ...?
EVBCompleteBarrierController name ?option value ...?
EVBIncompleteBarrierController name ?option value ...?
EVBDataLateController name ?option value ...?
EVBOutOfOrderController name ?option value ...?
EVBConnectionController name ?option value ...?
EVBFlowController name ?option value ...?

name configure option value ?...?

name update
      
```

<a name="AEN90573"></a>## DESCRIPTION

This package provides a family of controllers that interface
            between the model provided by
            [[r90296]]
            and the presentation views provided by
            [[r90050]].

All of these controller classes provide the following options:



`-model`An `EVBRestClient`  that will
                     be used as the model in the MVC triad.  The
                     client must be properly configured and the same client can,
                     and often will be shared between controllers.

`-view`Should be the view instance associated with the
                     specific controller (see
                     CONTROLLER VIEW PAIRS
                     below).

All controllers have exactly one public method: `update`
            which takes no parameters.  Prior to the first call of
            `update`
            the object must be fully configured with a valid
            `-model` and `-view`.  What
            `update` does is request the appropriate
            statistics from the model and then configure them in the
            appropriate option of the view.   In a normal application,
            this will be done periodically, e.g. from a rescheduled
            **after**.

<a name="AEN90599"></a>## CONTROLLER VIEW PAIRS

Each controller class in this package must be paired with the correct
         view or a compatible view like object.  The table below assumes you
         are pairing a controller with its compatible view in the
         EVBRestUI package.

<a name="AEN90603"></a>**Table 1. EVBRestControllers and Corresponding EVBRestUI Views**

| Controller | View |
| --- | --- |
| EVBInputStatsController | InputStatsView |
| EVBQueueStatsController | QueueStatsView |
| EVBBarrierStatsController | BarrierStatsView |
| EVBCompleteBarrierController | CompleteBarrierView |
| EVBIncompleteBarrierController | IncompleteBarrierView |
| EVBDataLateController | DataLateView |
| EVBOutOfOrderController | OutOfOrderView |
| EVBConnectionController | ConnectionView |
| EVBFlowController | FlowControlView |

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVBRESTClient | Up | evblite::evblite |

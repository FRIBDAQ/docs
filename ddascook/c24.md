|  |  |  |
| --- | --- | --- |
| The DDAS cookbook |
| Prev |  |  |


---

# <a name="ch.ddasevt"></a>Chapter 2. Reading ROOT-formatted DDAS data events

Once the evt files have been converted to ROOT format with the ddasdumper, an initial starting to point to access the information and analyze the data event by event follows.

<a name="AEN27"></a>```
R__LOAD_LIBRARY(/usr/opt/ddas/3.3-000/lib/libddaschannel.so)

void analyzer() {

  TFile* pFile = new TFile("runXYZ.root");
  TTree* pTree;
  pFile->GetObject("dchan", pTree);
  DDASEvent* pEvent = new DDASEvent;
  pTree->SetBranchAddress("ddasevent", &pEvent);

  for (int i=0; i<pTree->GetEntries(); ++i) {
    // access each single event from the tree
    pTree->GetEntry(i);

    // read data event-by-event
    for (int i=0; i<pEvent->GetNEvents(); i++){
      // get the variables
      ddaschannel *dchan = pEvent->GetData()[i];
      int crate  = dchan->GetCrateID();
      int slot   = dchan->GetSlotID();
      int chan   = dchan->GetChannelID();
      float energy = dchan->GetEnergy();
      float time   = dchan->GetTime();

    }
  }

}

            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| Introduction |  |  |

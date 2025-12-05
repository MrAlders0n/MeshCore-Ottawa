# MeshCore How To

The MeshCore How-To section provides simple, step-by-step guides for the most common tasks you’ll perform on the Ottawa MeshCore network.
Whether you’re sharing your contact URL, importing someone else’s, or tracing multi-hop routes across the mesh, each walkthrough is designed to be clear, visual, and easy to follow.

These instructions use the MeshCore mobile app and apply to both new and experienced users. More guides will be added as the platform grows and as the community discovers useful workflows.

## How to Share Your Contact URL

1. Open the MeshCore app and connect to your node.
2. Tap the **Signal** icon.  
   ![](images/MeshCore_GetContactID1.png){ width="300" }
3. Tap **Advert → To Clipboard**.  
   ![](images/MeshCore_GetContactID2.png){ width="300" }
4. Paste your contact URL anywhere you want to share it.

---

## How to Import a Contact URL

1. Open the app and connect to your node.
2. Tap the **three dots**.  
   ![](images/MeshCore_AddContactMan1.png){ width="300" }
3. Tap **Add Contact**.  
   ![](images/MeshCore_AddContactMan2.png){ width="300" }
4. Tap **Import from Clipboard Link**.  
   ![](images/MeshCore_AddContactMan3.png){ width="300" }
5. After a few seconds you will see:  
   **"Success - contact has been imported"**  
   ![](images/MeshCore_AddContactMan5.png){ width="300" }
6. A second popup appears:  
   **"New Contact Discovered \<NAME\>"**  
7. The contact is now added.

---

## How to Trace Route to a Node (1 Hop)

1. Open the app and connect.
2. Tap the **three dots**.  
   ![](images/MeshCore_TraceRoute1.png){ width="300" }
3. Tap **Tools**.  
   ![](images/MeshCore_TraceRoute2.png){ width="300" }
4. Tap **Trace Path - Manual**.  
   ![](images/MeshCore_TraceRoute3.png){ width="300" }
5. Tap the **plus button**.  
   ![](images/MeshCore_TraceRoute4.png){ width="300" }
6. Select a repeater and confirm.  
   ![](images/MeshCore_TraceRoute1Hop1.png){ width="300" }
7. You will see one repeater ID; this indicates a **1-hop trace**.  
   ![](images/MeshCore_TraceRoute1Hop2.png){ width="300" }
8. Tap **Trace Path**.

---

## How to Trace Route to a Node (2+ Hops)

1. Open the app and connect.
2. Tap the **three dots**.  
   ![](images/MeshCore_TraceRoute1.png){ width="300" }
3. Tap **Tools**.  
   ![](images/MeshCore_TraceRoute2.png){ width="300" }
4. Tap **Trace Path - Manual**.  
   ![](images/MeshCore_TraceRoute3.png){ width="300" }
5. Tap the **plus button**.  
   ![](images/MeshCore_TraceRoute4.png){ width="300" }

6. Select repeaters **in order**:
   - Choose the **forward path**  
   - Confirm  
   - Re-open the add menu and choose the **return path**
   - Or manually enter IDs:  
     Example: `d3, f3, d3`  
     ![](images/MeshCore_TraceRoute2Hop1.png){ width="300" }

7. Confirm both forward and return paths, then tap **Trace**.  
   ![](images/MeshCore_TraceRoute2Hop2.png){ width="300" }

8. View the results.  
   ![](images/MeshCore_TraceRoute2Hop3.png){ width="300" }

# What was changed?
Bill has more space now - it grew both vertically and horizontally thanks to removed gray paddings that were outdated (personal opinion, of course). Expandable/collapsable bill footer was introduced to give more space for items on demand (when you need to see items and not additional information). Bill actions were moved from a popover to a side menu. 

| How it looks?  |
| ------------- |
| <img width="800" height="600" alt="IMG_0359" src="https://github.com/user-attachments/assets/c9e81731-2b3d-4d1d-9fee-80374a70d4d0" /> |
| <img width="800" height="600" alt="IMG_0358" src="https://github.com/user-attachments/assets/3f7923fe-e604-4746-ba50-80f09a698086" /> |
| <img width="800" height="600" alt="IMG_0361" src="https://github.com/user-attachments/assets/511d3ece-4fd2-4c4d-8d48-fcc628b8720f" /> |
| <img width="800" height="600" alt="IMG_0360" src="https://github.com/user-attachments/assets/88bbabc1-3afb-4ee4-86e5-da2eced734bb" /> |

# iPOS
| Old  | New |
| ------------- |:-------------:|
| <img width="278" height="600" alt="IMG_1103" src="https://github.com/user-attachments/assets/f9004cc8-f6f4-49fe-b54c-880ea87f2845" /> | <img width="278" height="600" alt="IMG_1101" src="https://github.com/user-attachments/assets/25c0bb7e-d119-497b-b1d6-1423cc7b2df2" /> |
| <img width="278" height="600" alt="IMG_1104" src="https://github.com/user-attachments/assets/0668a23f-01dc-4a39-8dbb-8631c8b69436" /> | <img width="278" height="600" alt="IMG_1108" src="https://github.com/user-attachments/assets/f81e29b6-e222-4f13-9ae6-9aed4ae7cc9f" /> |
| <img width="278" height="600" alt="IMG_1105" src="https://github.com/user-attachments/assets/962ba4b4-3434-4af6-85e7-f53e807439c1" /> | <img width="278" height="600" alt="IMG_1109" src="https://github.com/user-attachments/assets/3be65920-0aab-4624-bf9c-dad270a1e6d9" /> |
| <img width="278" height="600" alt="IMG_1106" src="https://github.com/user-attachments/assets/6bc388c1-6795-40b9-ac23-22b9469d13a1" /> | <img width="278" height="600" alt="IMG_1110" src="https://github.com/user-attachments/assets/4c553e3f-7963-4a63-8bdd-e7fe08c0bc62" /> |

# Problems that were being solved
## Problem A
With some actions enabled, bill quickly becomes so squeezed that we are not able to fit even 
one item in it.
## Solution A
Make bill footer expandable so cashier would be able to collapse/expand it on demand. This selection is remembered on application level, so that even after POS is restarted it would remain collapsed/expanded. This is not applicable to self-checkout, where for each new sale footer is expanded.

| Old  | New |
| ------------- |:-------------:|
| <img width="800" height="600" alt="IMG_0032" src="https://github.com/user-attachments/assets/b5e09c55-657b-46fa-b61f-2d47be344b1a" />      | ![gif](https://github.com/user-attachments/assets/ebf3a04c-49eb-4c1c-bb54-24b0738262ca)     |

## Problem B
When you enable an action, you want to see it is enabled. If you do not see it, you might arrive at situation where you, e.g. remove VAT, go away from POS because customer asked something and when you came back, you forgot about removed VAT and make a sale like that. In old functionality, we show that VAT is removed as background text in the bill. But this text is visible only at the bottom, so if you have more items that fit into the bill (you need to scroll) you will not see that text without explicitly scrolling to the bottom.
## Solution B
Whenever you enable an action, a red badge counter appears on the bill actions menu to clearly indicate that something is enabled. When menu is opened, you can see enabled actions at the top.

| Old  | New |
| ------------- |:-------------:|
| ![gif2](https://github.com/user-attachments/assets/16986cd8-23d6-46bf-88e2-b055c421e0a4)      | ![gif3](https://github.com/user-attachments/assets/5e28f0a6-a4ea-4983-95b8-eb516ada91c4)     |

## Problem C
When enabling actions, user is thrown between various different presentation styles which is irritating and not consistent. For example, shared/parked bills are virtually the same functionality UI wise but when enabling park bill, you will be presented with an alert, whereas with share bill you will be presented with a side menu. This is applicable for other actions, you do not know what you will get when pressing on an action - an alert will pop up, nothing will happen, side menu will open or popover will be dismissed and a new view controller will be presented.
## Solution C
This was solved partially as more time is needed to rework all of the actions. The idea is that actions should be contained in the side menu, avoiding throwing user between popups/alerts/dismissals/etc. You select an action, it is enabled & side menu is dismissed OR if more information is needed, we slide forward to a new view in the side menu.

| Old  | New |
| ------------- |:-------------:|
| ![gifOLD](https://github.com/user-attachments/assets/bd0d4833-7d95-451e-ab5d-2529e5d903d5)      | ![gifNEW](https://github.com/user-attachments/assets/7e646662-e6aa-43d9-ab49-5657a616ea16)     |

# Additional notes
All of new views were made with SwiftUI which made process much easier & faster (kudos to Kasparas for making this available in project). Due to time constraints, not all actions were converted from old presentation styles to the new unified side menu presentation. This should be done as improvement in the future.


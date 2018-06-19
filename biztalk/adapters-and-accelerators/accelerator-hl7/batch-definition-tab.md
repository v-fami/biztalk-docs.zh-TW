---
title: 批次定義索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.batchdefinition
helpviewer_keywords:
- Batch Definition tab [Configuration Explorer]
- batching, configuring
- configuring, batching
ms.assetid: fe8685ef-5de5-4337-8691-8e4094056ace
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2270625a6e4512f2a99bea7a06812b601b48d44c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204510"
---
# <a name="batch-definition-tab"></a>批次定義索引標籤
您使用**批次定義**索引標籤上，以在 輸入批次處理，批次 / 出批次處理，批次，然後選取 為輸出批次處理的可用結構描述。  
  
 在**BTAHL7 Configuration 總管**對話方塊**批次定義**索引標籤上，執行下列動作：  
  
|使用|動作|  
|--------------|----------------|  
|**所需的片段**|選取下列其中一個選項：<br /><br /> -   **[是]**。 若要啟用片段。<br />-   **否**。 若要停用片段。 **注意：** 新合作對象，**片段所需**預設為**否**。|  
|**可復原交換所需的支援**|選取下列其中一個選項：<br /><br /> -   **True**。 若要啟用可復原交換支援。<br />-   **FALSE**。 若要停用可復原交換支援。 **注意：** 新合作對象，**片段所需**預設為**FALSE** ，才會啟用的值**片段所需**是**否**。|  
|**選取訊息**|選取您想要做為批次傳送，從 可用的訊息 視窗，然後按一下 向右箭號來移動訊息類型 (**>>**)。<br /><br /> 若批次內送通知訊息，您必須新增 ACK 訊息類型。 您所部署的 ACK 訊息結構描述。|  
|**選取訊息通知**|選取您想要的訊息類型[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]以做為批次傳送通知，從 [可用的訊息通知] 視窗中，然後按一下向右箭號來移動 (**>>**)。|
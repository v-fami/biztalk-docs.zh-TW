---
title: 如何使用連接埠類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, port types
- port types, deleting
- port types, Web
- port types, request-response
- orchestrations, ports
- port types, modifier
- port types
- ports, port types
- port types, one-way
ms.assetid: 78ac731e-c330-4888-a9ee-10523fef8ed0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e3b4307cb9d48679ae1b90f7e02dd0288ec2957
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257126"
---
# <a name="how-to-work-with-port-types"></a>如何使用連接埠類型
連接埠類型包含通訊模式、一組作業 (要求或回應)，以及可在其上運作這些作業的訊息類型。 模式可以是單向或要求-回應 (雙向)，且在該連接埠類型上定義的所有作業必須使用相同模式。 請注意，連接埠類型的方向不特定：方向是在個別連接埠上指定的。  
  
 連接埠類型的範圍由所定義**型別修飾詞**屬性。 連接埠類型可以是公用、專用或內部。 若為公用，則與協調流程互動的所有使用者皆可看到。 若為專用，則在相同專案和命名空間中的其他協調流程可以看到。 若為內部，則只有在專案內可以看到連接埠類型。 由於連接埠類型定義包括訊息類型，因此訊息類型的範圍必須包含使用它的任何連接埠類型之範圍。  
  
> [!NOTE]
>  連接埠類型可套用至任何數量的連接埠。 您可以將連接埠視為連接埠類型的執行個體。  
  
> [!NOTE]
>  連接埠類型基本上不具有通訊方向；您要在個別連接埠上設定方向。  
  
### <a name="to-add-a-request-response-port-type"></a>新增要求-回應連接埠類型  
  
1.  在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠類型**，然後按一下 [**新增要求-回應連接埠類型**。  
  
     **連接埠類型**節點，則會展開摺疊，並使用一個預設作業新增新的要求-回應連接埠類型。  
  
2.  指定連接埠類型的名稱。  
  
3.  定義一或多個連接埠作業。  
  
     您可以命名您的連接埠作業，不過，當您從其他專案選取連接埠作業時，只會看到它們顯示為「要求」和「回應」。 若您從其他專案選取連接埠作業，請確認其訊息類型正確。  
  
### <a name="to-add-a-one-way-port-type"></a>新增單向連接埠類型  
  
1.  在協調流程檢視] 視窗中，以滑鼠右鍵按一下**連接埠類型**，然後按一下 [**新單向連接埠類型**。  
  
     **連接埠類型**節點，則會展開摺疊，並使用一個預設作業新增新的單向連接埠類型。  
  
2.  指定連接埠類型的名稱。  
  
3.  定義一或多個連接埠作業。  
  
### <a name="to-add-a-web-port-type"></a>新增 Web 連接埠類型  
  
-   新增專案參考至包含 Web 服務的 Proxy 類別之組件。 如需詳細資訊，請參閱[建立 Web 連接埠](../core/creating-web-ports.md)。  
  
### <a name="to-remove-a-port-type"></a>移除連接埠類型  
  
-   在協調流程檢視] 視窗中，以滑鼠右鍵按一下要刪除，然後按一下 [連接埠類型**刪除**。  
  
    > [!NOTE]
    >  若連接埠類型正在使用中，刪除該連接埠類型會影響設定為使用它的所有連接埠之組態。  
  
    > [!NOTE]
    >  顯示為唯讀的項目定義在另一個協調流程中。  
  
### <a name="to-set-the-type-modifier-for-a-port-type"></a>設定連接埠類型的型別修飾詞  
  
-   在 [屬性] 視窗中，設定以下屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |型別修飾詞|決定連接埠類型的範圍：<br /><br /> 專用—存取此連接埠類型限於包含的模組。<br /><br /> 公用—存取此連接埠類型不受任何限制。<br /><br /> 內部—存取此連接埠類型限於相同專案中的模組。|  
  
## <a name="see-also"></a>另請參閱  
 [通訊模式](../core/communication-pattern.md)   
 [如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)   
 [協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)
---
title: 如何新增協調流程變數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
ms.assetid: c387cd56-5443-4de2-bbda-be34b95cbe71
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb8516ceb780e64c4f4a01370de0e7c40098f3da
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968828"
---
# <a name="how-to-add-orchestration-variables"></a>如何新增協調流程變數
[協調流程檢視] 視窗可讓您管理協調流程的屬性 (也稱為**服務**屬性)、 參數、 連接埠、 訊息，以及其他變數。 除了連接埠和訊息之外，您還可以建立整數變數、布林值變數、字串變數或 .NET 類別的變數。  
  
 您也可以使用 [協調流程檢視] 視窗來管理屬於您範圍的變數。  
  
### <a name="to-add-a-variable"></a>加入變數  
  
1.  在協調流程檢視 視窗中，以滑鼠右鍵按一下**變數**資料夾，然後按一下**新變數**。  
  
     **變數**資料夾，則會展開摺疊，並加入新的變數。  
  
2.  在 [屬性] 視窗的 [識別項] 屬性中輸入名稱，為變數命名。  
  
3.  讓變數和類型 (例如 .NET 類別) 產生關聯。  
  
    > [!NOTE]
    >  **類型**下拉式清單包含下列預先定義的變數類型：**布林**，**位元組**， **datetime**， **十進位**， **double**， **int16**， **int32**， **int64**， **sbyte****單一**，**字串**， **timespan**， **uint16**， **uint32**，和**uint64**。 您也可以存取.NET 資料型別和類別，藉由選取 **\<.NET 類別...\>** ，它會啟動**選取成品類型** 對話方塊。  
  
4.  如果您選取預先定義的變數類型，就可以選擇指定變數的初始值。 在 [屬性] 視窗中，設定**初始值**屬性。  
  
     若選取的類型是 .NET 類別，您可以選擇使用預設的建構函式。 在 [屬性] 視窗中，設定以下屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |**使用預設建構函式**|若 .NET 類別可以使用預設建構函式，此屬性會決定當您第一次使用變數時，是否要呼叫預設的建構函式：<br /><br /> True：將呼叫預設的建構函式。 這是在有預設建構函式可供使用時的預設值。<br /><br /> False：不會呼叫預設建構函式。您必須在運算式中呼叫建構函式，或將它指派給變數，才能在您的協調流程中使用該建構函式。|  
  
    > [!NOTE]
    >  如果預設建構函式需要輸入的參數，您可以設定**使用預設建構函式**至**False** ，然後呼叫建構函式從**指派**圖形; 針對範例中， `myVariable = myNamespace.myClass (param1, param2)`。  
  
    > [!NOTE]
    >  當您將變數新增至協調流程時，在完整定義之前，您會在協調流程中看到驚嘆號。 如果您在完整定義之前且驚嘆號仍然出現在協調流程中時刪除這個變數，就可以建立後再刪除協調流程參數，以強制讓協調流程移除這些驚嘆號。  
  
### <a name="to-remove-a-variable"></a>移除變數  
  
-   在協調流程檢視] 視窗中，以滑鼠右鍵按一下您想要移除，然後按一下 [的變數**刪除**。
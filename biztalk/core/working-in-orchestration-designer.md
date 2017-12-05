---
title: "使用協調流程設計師 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, saving
- deleting, orchestrations
- projects, orchestrations
- orchestrations, properties
- orchestrations, creating
- creating, orchestrations
- naming conventions, orchestrations
- orchestrations, naming conventions
- orchestrations, deleting
ms.assetid: 13e72b41-d9b6-4508-9a44-b3c7c1804f36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52eb574f9f6b55b784357ff03c05ccb23774fecb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="working-in-orchestration-designer"></a>使用協調流程設計師
啟動 BizTalk 專案之後，您可以建立新的協調流程，並將現有的協調流程加入專案。 請參閱下列程序，建立和儲存協調流程、在專案中加入或移除現有協調流程、變更協調流程名稱，以及設定協調流程屬性。  
  
### <a name="to-create-an-orchestration"></a>建立協調流程  
  
1.  在 方案總管 中，以滑鼠右鍵按一下專案名稱，請選取**新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目**對話方塊中，於**類別** 窗格中，按一下  **BizTalk 專案項目**，然後在**範本** 窗格中，按一下**BizTalk 協調流程**。  
  
3.  在**名稱**方塊 對話方塊底部提供的協調流程的名稱，然後按**新增**。  
  
     [協調流程設計師] 中便會建立並顯示新的協調流程，而 [方案總管] 中則會建立並顯示對應的 .odx 檔案。  
  
### <a name="to-add-an-existing-orchestration-to-a-project"></a>將現有的協調流程加入至專案  
  
1.  在 方案總管 中，以滑鼠右鍵按一下專案名稱，請按一下**新增**，然後按一下 **現有項目**。  
  
2.  在**加入現有項目**對話方塊中，瀏覽至包含協調流程的目錄中，選取協調流程，，然後按一下**新增**。  
  
     協調流程便會加入專案中。  
  
    > [!NOTE]
    >  當您加入現有檔案時，會將該檔案複製到專案中 (並非只是加入檔案的參考)。如果您變更專案中的檔案，原始檔案會保持不變。  
  
### <a name="to-change-the-name-of-an-orchestration"></a>變更協調流程的名稱  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下您想要變更，然後再按一下.odx 檔案**重新命名**。  
  
2.  輸入想要的新檔案名稱，然後按 ENTER。  
  
    > [!NOTE]
    >  當您變更.odx 檔案的名稱時，您也可以按一下設計介面，以顯示 [屬性] 視窗，然後變更的值變更協調流程類型的名稱**Typename**屬性協調流程。  
  
### <a name="to-save-an-orchestration"></a>儲存協調流程  
  
-   在**檔案**功能表上，按一下 **儲存\<協調流程的名稱\>**。  
  
    > [!NOTE]
    >  協調流程檔案會儲存為 utf-8。  結構描述、 對應和管線會儲存為 utf-16。  
  
### <a name="to-remove-an-orchestration-from-a-project"></a>從專案移除協調流程  
  
-   在 方案總管 中，以滑鼠右鍵按一下您想要移除，然後按一下 的檔案**從專案移除**。  
  
    > [!NOTE]
    >  若要從專案移除協調流程並永久刪除檔案，按一下**刪除**改為。  
  
### <a name="to-include-an-excluded-orchestration-in-a-project"></a>在專案中包含已排除的協調流程  
  
-   在 方案總管 中，按一下 **全部顯示**工具列按鈕，以滑鼠右鍵按一下.odx 檔案，並選取**加入至專案**。  
  
### <a name="to-set-orchestration-properties"></a>設定協調流程屬性  
  
1.  按兩下專案中的 .odx 檔案，或選取 [處理區域] 中包含協調流程的索引標籤，以開啟協調流程。  
  
2.  在 [協調流程檢視] 視窗中，選取**協調流程屬性**。  
  
     -或者-  
  
     按一下**流程領域**協調流程設計介面的背景。  
  
3.  在 [屬性] 視窗中，指定下列屬性。 請注意，某些屬性只有在特定情況下才會出現。  
  
    > [!NOTE]
    >  協調流程、連接埠類型及多部分訊息類型的名稱在模組的範圍內必須是唯一的。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |批次|決定「不可部分完成交易」的協調流程是否能和其他執行個體一起，以批次方式執行。|  
    |補償|指定要在協調流程上執行的補償類型。|  
    |隔離等級|決定交易式協調流程可在並行交易之間存取資料的權限等級。|  
    |模組可匯出|決定是否可以將模組匯出至 BPEL4WS。|  
    |模組 XML 目標命名空間|在匯出類型至 BPEL4WS 時所使用的 XML 目標命名空間。|  
    |命名空間|決定將包括協調流程和協調流程類型之容納模組的名稱。|  
    |協調流程可匯出|指出此協調流程是否可供匯出至 BPEL4WS。|  
    |協調流程 XML 目標命名空間|在匯出此協調流程至 BPEL4WS 時所使用的 XML 目標命名空間。|  
    |重試|指定是否在交易式協調流程失敗時進行重試。|  
    |逾時|交易式協調流程閒置多久之後即視為失敗的時間 (以秒為單位)。|  
    |交易識別項|交易式協調流程的唯一識別項。|  
    |[交易類型]|決定協調流程是不可部分完成的交易、長時間執行的交易，或者不是交易。|  
    |型別修飾詞|決定協調流程層級變數的範圍：<br /><br /> 私用：只限包含的模組存取此協調流程。<br /><br /> 公用：存取此協調流程不受任何限制。<br /><br /> 內部：只限相同專案中的模組存取此協調流程。|  
    |類型名稱|決定此協調流程在包含的模組中的名稱。 **注意：**如果您使用的根層級命名空間，與相同類型名稱時可能會收到錯誤來自協調流程設計師定義訊息，並根據類型名稱，嘗試執行變數指派的運算。 例如，如果您指定類型名稱的系統，然後定義訊息和變數，如下 System.String，您可能會收到錯誤。|  
  
## <a name="see-also"></a>請參閱  
 [協調流程圖形](../core/orchestration-shapes.md)   
 [如何新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md)   
 [如何新增參數至協調流程](../core/how-to-add-parameters-to-orchestrations.md)   
 [如何使用選取成品類型對話方塊](../core/how-to-use-the-select-artifact-type-dialog-box.md)
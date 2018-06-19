---
title: 如何控制結果清單的大小 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- results list [Orchestration Debugger], deleting columns
- results list [Orchestration Debugger], limiting list size
- Orchestration Debugger, results list
- results list [Orchestration Designer]
- results list [Orchestration Debugger], adding columns
ms.assetid: 4d41003f-5ea9-4599-8ec0-737c342ffdbd
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80787e4c7dbac57aca9c787943846e924a1a7870
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249734"
---
# <a name="how-to-control-the-size-of-the-results-list"></a>如何控制結果清單的大小
在**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，查詢結果 窗格包含這麼多的資料行的資訊，您需要捲動來檢視它們。 您可以新增或移除窗格中的欄位，只顯示您需要的資訊。 若要新增或移除資料行，以滑鼠右鍵按一下 [查詢結果] 窗格，然後按一下的任何部分**新增/移除欄位**操作功能表上。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。  
  
### <a name="to-add-or-remove-columns-in-the-results-list"></a>在結果清單中新增或移除欄位  
  
1.  以滑鼠右鍵按一下任何資料格中**查詢結果**清單，然後再按**新增/移除欄位**操作功能表上。  
  
    > [!NOTE]
    >  已存在於結果清單中的項目會出現在下方的右邊**顯示的資料行**。 不會出現在結果清單中的項目會出現在左側**可用的資料行**。  
  
2.  若要加入資料行，選取其中一個項目從**可用的資料行**按一下**新增**若要將該資料行移到清單**顯示的資料行**。  
  
3.  若要移除資料行，選取其中一個項目從**顯示的資料行**按一下**移除**若要將該資料行移到清單**可用的資料行**。  
  
 透過使用建立或執行查詢時提供的篩選，可以控制查詢傳回的結果數。  
  
## <a name="columns-in-the-query-results-list"></a>查詢結果清單中的欄位  
 查詢結果會顯示於產生查詢之檢視下方的 [查詢結果] 窗格中。 您無法直接存取結果清單。 快顯功能表會顯示您可對目前作用中之檢視內選取的記錄執行的所有動作。 例如，若記錄包括「服務執行個體識別碼」，則會出現服務相關的動作。 如果有「訊息識別碼」，則會顯示訊息相關動作。  
  
 因為您可能不需要此完整清單中包含的所有資訊，您可以僅選取想要檢視的欄位，或取代您移除的欄位。 當您依照時間排序結果清單時，執行個體會排序至毫秒，即使毫秒沒有出現在清單上也一樣。 當您重複使用已儲存的查詢時，每次執行查詢，結果都只會顯示選取的欄位。  
  
 下表顯示結果清單上所顯示的完整項目清單。  
  
|||  
|-|-|  
|**服務或訊息欄位**|**說明**|  
|服務名稱|服務執行個體的名稱。|  
|事件類型|服務類型 (例如，傳訊 (報告為「管線」)、協調流程、傳輸配接器)。|  
|錯誤描述|錯誤發生時的描述。|  
|State|執行查詢時的作業狀態。|  
|錯誤碼|錯誤發生時的代碼。|  
|解密憑證|顯示和訊息或服務相關的憑證資訊。|  
|有效期間|完成作業所需的時間。|  
|連接埠名稱|與執行個體流程相關的連接埠。|  
|簽章|訊息的數位簽章資訊。|  
|大小|訊息大小 (位元組)。|  
|Start Time|作業開始的時間。|  
|結束時間|作業結束的時間。|  
|部分計數|訊息的部分數目。|  
|Party|開始作業的合作對象識別碼。|  
|URI|發起合作對象的 URI。|  
|TimeStamp|作業開始的時間。|  
|Host|執行服務執行個體的 BizTalk 主控件名稱。|  
|組件名稱|實作服務執行個體的 .NET 組件名稱。|  
|組件版本|相關組件的版本編號。|  
|部署時間|部署服務執行個體組件到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的時間。|  
|活動識別碼|識別唯一的服務執行個體活動 (例如，管線/協調流程所傳送/接收具有相同識別碼的訊息)。|  
|服務執行個體識別碼|識別服務執行個體執行的「全域唯一識別碼」(GUID)。|  
|訊息執行個體識別碼|識別訊息執行個體的「全域唯一識別碼」(GUID)。|  
|服務識別碼|識別服務的「全域唯一識別碼」(GUID)。|  
|服務類別|類別的類型 (管線或協調流程)。|  
|服務類別識別碼|識別服務 (例如，協調流程) 的服務獨立 GUID。|  
|圖示|結果列的圖示。|  
|配接器|作業使用的配接器。|
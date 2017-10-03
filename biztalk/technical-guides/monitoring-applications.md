---
title: "監視應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4be98ba2-6acd-4dee-b6ea-db71bbd368f0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bead22f33bbe38cb8deac3a201121438d344c09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-applications"></a>監視應用程式
設定 Microsoft System Center Operations Manager 來監視 BizTalk 應用程式通常可以分成漸進式的四個步驟程序，如下所示：  
  
1.  **修改現有的規則和/或複製的規則，以自訂的管理組件來監視自訂 BizTalk 應用程式**  
  
     您必須將複製其中許多規則多次。 如果您要監視的數字的檔案共用，例如，這是大小寫。 在此案例中，您會複製基底規則一次的每個檔案共用上的描述欄位中加入的檔案共用位址**準則**規則 索引標籤。 藉由新增地址，Operations Manager 將會引發警示的每個個別的檔案共用。 當您複製現有的規則時，請確定您選取**啟用**規則停用覆寫此規則，或您會收到重複的警示。  
  
     您應該將它加入至您所建立的每個規則的另一個項目位於知識資訊**知識庫**規則屬性 索引標籤。 這項資料會附加至 Operations Manager 會送出警示時，會引發通知。 包含可協助解決此錯誤的步驟，這項功能的能力會變得清楚。  
  
2.  **建立每個已定義的規則動作**  
  
     在建立或修改規則實際上是程序的第一個步驟。 下一個步驟是要採取某些動作，根據該規則。 如果沒有採取任何動作不以規則然後其實並沒有差別曾經監視事件。 最常執行的動作是要警示的操作員或系統管理員發生錯誤。 Operations Manager 也提供數個其他的事件觸發時，可以使用的動作。 這些動作包括：  
  
    -   啟動指令碼  
  
    -   傳送簡易網路管理通訊協定 (SNMP) 陷阱 （在 SNMP 代理程式監視的各種裝置上的網路和網路主控台工作站的報表中的活動）  
  
    -   傳送通知給通知群組  
  
    -   執行命令或批次檔  
  
    -   更新狀態變數  
  
    -   檔案傳輸  
  
    -   Managed 程式碼組件上呼叫方法  
  
3.  **建立自動化手動工作的反覆程序**  
  
     下一個步驟是反覆的程序，並移出基本警示機制。 使用 Operations Manager 可以叫用指令碼和.NET 程式碼，自動化手動工作引發的事件為基礎的程序是功能強大且時間儲存功能。 這個範例是執行指令碼來自動啟動的通訊埠，如果記錄已停用 / 停止事件訊息。 此程序，因為可以自動化許多處理序。  
  
4.  **使用來自動化手動工作的臨界值規則**  
  
     在處理下一個步驟是超越反應靈敏的警示，並使用臨界值規則。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理組件程式預設不包含任何臨界值規則。 這是因為這類規則通常專用於自訂應用程式，以及每個應用程式不同。 臨界值意自訂應用程式的相關商務規則，並提供主動式方法來監視系統。 您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供使用效能分析的記錄檔 (PAL) 工具來定義規則的臨界值範本。  
  
     臨界值規則的範例是在伺服器上的 Cpu 一致的方式執行時超過 75%一段特定時間量值。 這可能表示您需要向外擴充系統。 尚未另一個範例是您用來建立一組唯一的計數器會監視的臨界值規則。 此規則無法再叫用先前設定的備份伺服器上的 BizTalk 主控件執行個體初始化期間需求較高的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [監控 BizTalk Server 與 System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)
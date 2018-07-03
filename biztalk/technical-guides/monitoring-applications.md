---
title: 監視應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4be98ba2-6acd-4dee-b6ea-db71bbd368f0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d1a7e4e0d4cb0f4e6899159da6c6c06a83e9165
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010291"
---
# <a name="monitoring-applications"></a>監視應用程式
設定 Microsoft System Center Operations Manager 來監視 BizTalk 應用程式通常可以分成往下漸進式的四個步驟程序，如下所示：  
  
1. **修改現有的規則和/或複製的規則，以自訂的管理組件來監視自訂的 BizTalk 應用程式**  
  
    您必須複製其中許多規則多次。 如果您要監視多個檔案共用，比方說，這會是大小寫。 在此案例中，您會複製基底規則一次的每個檔案共用上的 描述 欄位中新增的檔案共用位址**準則**規則 索引標籤。 藉由新增地址，Operations Manager 將會引發每個個別的檔案共用的警示。 當您複製現有的規則時，請確定您選取**啟用**停用的規則覆寫此規則，或您會收到重複的警示。  
  
    您應該將它新增至您所建立的每個規則的另一個項目位於知識資訊**知識庫**規則屬性 索引標籤。 這項資料會附加至 Operations Manager 會傳送出警示時，會引發通知。 當您加入可能有助於解決此錯誤的步驟時，便會清楚的這項功能強大。  
  
2. **建立針對每個已定義的規則動作**  
  
    建立或複製規則其實處理程序的第一個步驟。 下一個步驟是採取某些動作，根據該規則。 如果沒有採取任何動作不根據規則則怪罪則不斷監視事件。 最常執行的動作為警示操作員或系統管理員所發生的錯誤。 Operations Manager 也會提供數個觸發事件時，可以使用其他動作。 這些動作包括：  
  
   -   啟動指令碼  
  
   -   傳送簡易網路管理通訊協定 (SNMP) 陷阱 （在 SNMP 代理程式來監視各種裝置上的網路和網路主控台工作站的報表中的活動）  
  
   -   傳送通知給通知群組  
  
   -   執行命令或批次檔  
  
   -   更新狀態變數  
  
   -   傳輸檔案  
  
   -   在 managed 程式碼組件上呼叫方法  
  
3. **建立反覆的程序，以將手動工作自動化**  
  
    下一個步驟是反覆的程序，並移出基本的警示機制。 使用 Operations Manager 能夠叫用指令碼和.NET 程式碼，以引發的事件為基礎的手動工作自動化的程序會是功能強大且時間的儲存功能。 這個範例是執行指令碼來自動啟動連接埠，如果記錄已停用 / 停止事件訊息。 此程序是反覆的因為可以自動化許多程序。  
  
4. **使用臨界值規則來將手動工作自動化**  
  
    處理的下一個步驟是超越消極反應式的警示，並使用臨界值規則。 根據預設，BizTalk Server 管理組件不包含任何臨界值規則。 這是因為這類規則通常專用於自訂的應用程式，並有不同的每個應用程式。 臨界值包含自訂的應用程式的相關商務規則，並提供主動監視系統。 您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所提供的效能分析的記錄檔 (PAL) 工具，來定義規則的臨界值範本。  
  
    測量在伺服器上的 Cpu 持續執行 75%以上一段特定時間時為這類的臨界值規則範例。 這可能表示您需要相應放大系統。 還有另一個範例是您用來建立一組唯一的計數器會監視的臨界值規則。 此規則能再叫用程式碼來初始化先前設定的備份伺服器上的 BizTalk 主控件執行個體的高需求期間。  
  
## <a name="see-also"></a>另請參閱  
 [使用 System Center Operations Manager 2007 監視 BizTalk Server](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)
---
title: 設定 EDI 和 AS2 狀態報告 |Microsoft Docs
description: 建立 EDI 或 AS2 狀態報告查詢運算式中，並選取您想要在 BizTalk Server 中的報表中顯示的資料
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6490864d-f1e6-4932-aefb-c332a595aad7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4981067305a6b1de57c393cea7d49323933a0ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972799"
---
# <a name="configure-an-edi-and-as2-status-report"></a>設定 EDI 和 AS2 狀態報告
您已啟用 EDI 或 AS2 狀態報告，顯示狀態報告之後，您想從**EDI 狀態報告**或是**EDIINT 狀態報告**一節**群組中樞**索引標籤**群組概觀**頁面中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 當您顯示狀態報告時，您會看到預設的資料集。 您可以設定狀態報告的下列各方面：  
  
- 執行來決定狀態報告之資料範圍的查詢運算式，例如日期範圍、資料的方向 (接收或傳送) 或狀態值 (「已接受」、「已拒絕」、「全部」等)。  
  
- 顯示在狀態報告窗格中的資料型別，這是由報告中的資料行所決定。  
  
  > [!NOTE]
  >  一旦啟用狀態報告後，所有的狀態都會儲存在儲存區中。 透過自訂查詢運算式或狀態資料行，您就可以定義顯示的已儲存資料。  
  
  有五個不同 EDI 和 AS2 狀態報告 (請參閱[類型的 EDI 和 AS2 狀態報告](../core/types-of-edi-and-as2-status-reports.md))。 雖然每種報告中的資料不同，但設定報告的方式都相同。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
## <a name="configure-the-status-report-query-expression"></a>設定狀態報告查詢運算式  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**BizTalk 群組**節點，查看**群組概觀**窗格。  
  
2. 在底部**群組中樞**索引標籤中**群組概觀**窗格中，按一下您想要設定，例如的狀態報告**EDI 交換和相互關聯的 ACK 狀態**。  
  
3. 在 **查詢運算式**區域的狀態報告窗格中，確認您想要定義查詢的所有篩選準則都會出現。 否則，請按一下中的空白資料列的向下箭號**欄位名**底部的 查詢運算式中，並選取您想要加入查詢運算式的準則的所有篩選的資料行。 您可以藉由選取該列，然後按一下 刪除篩選準則列**刪除**鍵盤上的按鈕。  
  
4. 確認篩選條件運算式的值是否是您需要的。 如果沒有，請按一下 向下的箭號**運算子**選取查詢作業，然後輸入適當的值中的資料行**值**資料行。  
  
   > [!NOTE]
   >  運算子和值可用於查詢運算式中的篩選準則所述[類型的 EDI 和 AS2 狀態報告](../core/types-of-edi-and-as2-status-reports.md)並**EDI-AS2 狀態報告 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
5. 若要執行查詢，顯示 [狀態] 報告，根據篩選準則中，按一下**執行查詢**。  
  
6. 若要將查詢運算式儲存成.btq 檔案中，按一下**另存新檔**、 指定的資料夾並輸入的檔案名稱，然後按一下**儲存**。  
  
7. 若要開啟儲存的.btq 檔案，請按一下**開啟查詢**。  
  
## <a name="configure-the-type-of-data-displayed-in-the-status-report-pane"></a>設定顯示在狀態報告窗格中的資料類型  
  
1.  以滑鼠右鍵按一下狀態報告窗格中，狀態結果區域，然後按一下**新增/移除欄位**。  
  
2.  若要將狀態類別加入顯示的資料行清單中，按一下 中的資料行**可用的資料行**清單，然後再按**新增**。  
  
3.  若要移除狀態類別從顯示的資料行清單中，按一下 資料行**顯示的資料行**清單，然後再按**移除**。  
  
## <a name="see-also"></a>另請參閱  
 [監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)   
 [啟用 EDI 和 AS2 狀態報告](../core/enabling-edi-and-as2-status-reports.md)   
 [顯示 EDI 或 AS2 狀態報告](../core/displaying-an-edi-or-as2-status-report.md)
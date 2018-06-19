---
title: 步驟 2： 建立 Contoso 3A2 價格與可用性查詢回應案例中使用 BizTalk 總管 中的連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating ports
ms.assetid: e0b12a96-e799-47ac-8293-7de10662bdf0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64101a31b1d1ea9c7af00471c5d764a1d8cfe598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210142"
---
# <a name="step-2-creating-ports-for-the-contoso-3a2-price-and-availability-queryresponse-scenario"></a>步驟 2： 為 Contoso 3A2 價格與可用性查詢/回應實例建立連接埠
在此步驟中，您可以建立使用由 BizTalk Server 所提供的 SQL 配接器的傳送埠。 您可以使用 SQL 連接埠傳送並接收往返於 Contoso ERP 系統的「3A2 價格與可用性」回應。  
  
### <a name="to-configure-a-send-port-using-the-sql-adapter"></a>使用 SQL 配接器設定傳送埠  
  
1.  在 Visual Studio 中，在**檢視**功能表上，按一下  **BizTalk 總管**。  
  
2.  在 BizTalk 總管 中，以滑鼠右鍵按一下**傳送埠**，然後按一下 **新增傳送埠**。  
  
3.  在 [建立新傳送埠] 對話方塊中，選取**靜態請求-回應連接埠**從下拉式清單，然後按一下**確定**。  
  
4.  在 [靜態請求-回應傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**3A2SQLReqResponseSendPort**。  
  
5.  在 [屬性] 視窗中**一般**標題之下，選取**SQL**為**傳輸類型**。  
  
6.  在**位址 URI**方塊中，按一下省略符號按鈕 (**...**).  
  
7.  在 [SQL 傳輸屬性] 對話方塊中，按一下省略符號按鈕 (**...**) 旁邊**連接字串**方塊。  
  
8.  在 [資料連結屬性] 對話方塊中**選取或輸入伺服器名稱**方塊中，輸入**localhost**。  
  
9. 選取**使用 Windows NT 整合式安全性**。  
  
10. 在**選取的資料庫伺服器上**方塊中，選取**Contoso**，然後按一下 **確定**。  
  
11. 在 [SQL 傳輸屬性] 對話方塊中**文件目標命名空間**方塊中，輸入**http://Contoso.com/Price**。  
  
12. 在**回應文件根項目名稱**方塊中，輸入**rootPriceResponse**，然後按一下 **確定**。  
  
13. 在 靜態請求-回應傳送埠屬性 對話方塊的左窗格中，按一下 **傳送**。  
  
14. 在 [靜態請求-回應傳送埠屬性-組態-傳送-一般] 對話方塊中**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
15. 在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.XMLReceive**，然後按一下 **確定**。  
  
16. 在 BizTalk 總管 中，以滑鼠右鍵按一下**3A2SQLReqResponseSendPort**，然後按一下 **登錄**。 以滑鼠右鍵按一下它，然後按一下**啟動**。  
  
## <a name="see-also"></a>另請參閱  
 [建立與修改 Contoso 私用程序](creating-and-modifying-the-private-process-for-contoso.md)
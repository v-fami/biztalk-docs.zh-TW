---
title: 步驟 3： 測試移轉的 Application6 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (RFC)
- migration
ms.assetid: 1b1ee59c-a5a3-442d-af2c-0fc4817f3063
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ebc175053b7afa1f3c360623b0230809db17bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216798"
---
# <a name="step-3-test-the-migrated-application"></a>步驟 3： 測試已移轉的應用程式
![步驟 3 之 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您會測試已移轉的應用程式叫用 SD_RFC_CUSTOMER_GET RFC。 若要這樣做，您卸除使用 vPrev SAP 配接器所產生的結構描述的要求訊息。  
  
## <a name="prerequisites"></a>必要條件  
  
-   將 BizTalk 協調流程中的邏輯連接埠對應至實體連接埠，BizTalk Server 管理主控台中設定的 BizTalk 應用程式。  
  
-   設定要用於 Wcf-custom 傳送埠以 WCF 為基礎的 BizTalk 應用程式[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="to-test-the-migrated-application"></a>若要測試已移轉的應用程式  
  
1.  從 [SAP_RFC_Migration] 資料夾中，複製 Input.xml 要求訊息。 此要求訊息符合 vPrev SAP 配接器所產生的結構描述。 使用 輸出對應，WCF 自訂傳送連接埠轉換以 WCF 為基礎的結構描述符合[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]並將它傳送至 SAP 系統。  
  
    ```  
    <ns0:SD_RFC_CUSTOMER_GET_Request xmlns:ns0="http://schemas.microsoft.com/BizTalk/2003">  
      <KUNNR>0000001390</KUNNR>  
      <NAME1/>  
      <CUSTOMER_T/>  
    </ns0:SD_RFC_CUSTOMER_GET_Request>  
    ```  
  
2.  貼上要對應至檔案的資料夾的要求訊息的接收位置。  
  
3.  協調流程會使用要求訊息，並將它傳送至 SAP 系統。 收到來自 SAP 系統的回應結構描述中，並符合以 WCF 為基礎的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 使用輸入的對應，WCF 自訂傳送連接埠轉換為 vPrev SAP 配接器的結構描述。 從 SAP 系統的回應會儲存到其他的協調流程中定義的檔案位置。 先前的要求訊息的回應是：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <ns0:SD_RFC_CUSTOMER_GET_Response xmlns:ns0="http://schemas.microsoft.com/BizTalk/2003">  
      <CUSTOMER_T>  
        <KUNNR>0000001390</KUNNR>   
        <ANRED>Firma</ANRED>   
        <NAME1>Contoso, Ltd.</NAME1>   
        <PFACH />   
        <STRAS>Strasse 4567</STRAS>   
        <PSTLZ>50000</PSTLZ>   
        <ORT01>Aachen</ORT01>   
        <TELF1>0123-45678</TELF1>   
        <TELFX>0123-56789</TELFX>   
      </CUSTOMER_T>  
    </ns0:SD_RFC_CUSTOMER_GET_Response>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2： 移轉 SAP RFC BizTalk 專案](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)
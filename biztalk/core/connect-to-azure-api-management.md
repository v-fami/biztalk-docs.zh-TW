---
title: "發行 SOAP 端點 API 管理 |Microsoft 文件"
description: "使用 Feature Pack 1 和 Feature Pack 2 公開 BizTalk WCF 基本 HTTP 接收位置為 API 管理中的 SOAP 端點。 您可以使用 BizTalk 管理主控台中，執行此動作，或在 Azure 入口網站中貼上您直接在 API 管理中的端點。"
ms.custom: 
ms.date: 11/21/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: valrobb
manager: anneta
ms.openlocfilehash: 8ac1e824ad11ef18eac6deb1252101bbd1ec187a
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="publish-biztalk-soap-endpoints-in-api-management"></a>在 API 管理中發佈 BizTalk SOAP 端點

將 BizTalk SOAP 端點公開為 Azure API 管理中的服務。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能組件 1**，您可以公開從 BizTalk 應用程式開發介面管理透過 SOAP 端點。 您可以在 Azure 入口網站中使用 API 管理。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以公開 Wcf-basichttp 接收位置做為使用 BizTalk 管理 的 Azure API 管理中的端點。 

> [!TIP]
> [什麼是 API 管理？](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts)是了解，並深入了解這項 Azure 服務的絕佳資源。

## <a name="prerequisites"></a>必要條件
* 設定並設定[Azure API 管理](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)
* 建立[虛擬網路](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet)BizTalk 電腦與 API 管理執行個體之間
* 安裝[功能套件 2](https://aka.ms/bts2016fp2) BizTalk 伺服器上

## <a name="create-using-api-management-in-azure-portal"></a>建立在 Azure 入口網站中使用 API 管理 
1. 在[Azure 入口網站](https://portal.azure.com)，開啟您的 API 管理，然後選取**Api**:

    ![選取的 BizTalk 應用程式開發介面](../core/media/select-api-for-biztalk.png)
    
2. 選取**WSDL**:

    ![選取 wsdl biztalk 應用程式開發介面](../core/media/select-wsdl-biztalk-api.png)
    
3. 設定您的 WSDL 內容： 

    1. **WSDL 規格**： 輸入 BizTalk SOAP 端點的完整 URI。 例如，輸入類似`http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`或`http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`。  

    2. **SOAP 傳遞**或**REST 的 SOAP** ： 選取您的喜好設定： 
        * **其餘的 SOAP**： 從現有的 SOAP web 服務建立 REST 架構 HTTP Api
        * **SOAP 傳遞**： 做為 SOAP API 的 proxy 

    3. 輸入慣用**顯示名稱**，**名稱**，**描述**， **API Url 尾碼**，**產品**，和**版本**。

    完成時，WSDL 組態看起來像下面這樣： 

    ![建立從 WSDL BizTalk 應用程式開發介面](../core/media/create-api-from-wsdl-biztalk.png)

4. 選取 [建立]。

## <a name="create-using-the-biztalk-administration"></a>建立使用 BizTalk 管理

> [!NOTE] 
> 這項功能支援 Wcf-basichttp 接收位置。 

1. 在 BizTalk 管理主控台，以滑鼠右鍵按一下您 Wcf-basichttp 接收位置，然後選取**發行至 API 管理**:  

    ![發行功能表選項](../core/media/publish-to-api-management-option.png)
 
2. 設定您的 API 管理內容： 

    1. **登入**您 Azure 訂用帳戶中，選取**訂用帳戶**和**資源群組**具有您 API 管理服務，然後選取您的服務。

    2. **WSDL 規格連結**自動填入您的 WSDL 檔案。 取代**localhost** DNS 名稱或 IP 位址的 BizTalk Server。 

    3. 選取**SOAP 傳遞**或**REST 的 SOAP**:  
        * **其餘的 SOAP**： 從現有的 SOAP web 服務建立 REST 架構 HTTP Api
        * **SOAP 傳遞**： 做為 SOAP API 的 proxy 

        API 可以藉由變更發佈這兩種方式**API URL 尾碼**，，再發行一次使用不同的應用程式開發介面型別。

    4. **API 名稱**自動填入接收位置名稱。

    5. 選取**API URL 尾碼**以供取用者的 api。 

    完成時，您的內容看起來如下所示：  
    ![發行至應用程式開發介面 視窗](../core/media/api-management-publish-window.png)


3. 選取**發行**。 成功時，接收位置會顯示在 API 管理中的服務為[Azure 入口網站](https://portal.azure.com)。 

## <a name="do-more"></a>執行其他動作
Azure API 管理是功能強大服務會使用有大量的 Azure 服務，包括邏輯應用程式。 API 管理包括許多功能，包括 速率限制和配額，可以存取您的應用程式開發介面，快取，以及更多。 請參閱[API 管理是什麼？](https://docs.microsoft.com/en-us/azure/api-management/api-management-key-concepts)若要開始使用。

## <a name="see-also"></a>另請參閱
[設定 Feature Pack](configure-the-feature-pack.md)

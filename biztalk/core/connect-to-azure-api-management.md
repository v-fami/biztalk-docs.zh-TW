---
title: 發佈 SOAP 端點的 API 管理 |Microsoft Docs
description: 使用 Feature Pack 1 和 Feature Pack 2 以公開 BizTalk WCF 基本 HTTP 接收位置做為 API 管理中的 SOAP 端點。 您可以使用 BizTalk 管理主控台中，執行此動作，或在 Azure 入口網站中貼上您直接在 API 管理中的端點。
ms.custom: ''
ms.date: 11/21/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: 2
author: MandiOhlinger
ms.author: valrobb
manager: anneta
ms.openlocfilehash: c8bdb3cb3f2d0fc247ea607a1b34623006315754
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993711"
---
# <a name="publish-biztalk-soap-endpoints-in-api-management"></a>在 API 管理中發佈 BizTalk SOAP 端點

公開您的 BizTalk SOAP 端點做為 Azure API 管理中的服務。 

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 1**，您可以公開 （expose) 透過 「 API 管理，從 BizTalk SOAP 端點。 您可以在 Azure 入口網站中使用 API 管理。 

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以公開 Wcf-basichttp 接收位置使用 BizTalk 管理的 Azure API 管理中的端點。 

> [!TIP]
> [什麼是 API 管理？](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)是了解並深入了解這項 Azure 服務的絕佳資源。

## <a name="prerequisites"></a>必要條件
* 設定及安裝[Azure API 管理](https://docs.microsoft.com/azure/api-management/api-management-get-started)
* 建立[虛擬網路](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet)BizTalk 電腦與 API 管理執行個體之間
* 安裝[Feature Pack 2](https://aka.ms/bts2016fp2) BizTalk Server 上

## <a name="create-using-api-management-in-azure-portal"></a>建立在 Azure 入口網站中使用 API 管理 
1. 在  [Azure 入口網站](https://portal.azure.com)，開啟您的 API 管理，然後選取**Api**:

    ![選取 biztalk 的 API](../core/media/select-api-for-biztalk.png)
    
2. 選取  **WSDL**:

    ![選取 wsdl biztalk api](../core/media/select-wsdl-biztalk-api.png)
    
3. 設定您的 WSDL 屬性： 

   1. **WSDL 規格**： 輸入您的 BizTalk SOAP 端點的完整 URI。 例如，輸入類似`http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`或`http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`。  

   2. **SOAP 傳遞**或是**SOAP 至 REST** ： 選取您的喜好設定： 
       * **SOAP 到 REST**： 從現有的 SOAP 式 web 服務建立 REST 架構 HTTP Api
       * **SOAP 傳遞**： 做為 SOAP API 的 proxy 

   3. 輸入您慣用**顯示名稱**，**名稱**，**描述**， **API Url 尾碼**，**產品**，並**版本**。

      完成時，您的 WSDL 設定看起來像下面這樣： 

      ![從 WSDL BizTalk 建立 API](../core/media/create-api-from-wsdl-biztalk.png)

4. 選取 [建立]。

## <a name="create-using-the-biztalk-administration"></a>建立使用 「 BizTalk 管理

> [!NOTE] 
> 這項功能支援 Wcf-basichttp 接收位置。 

1. 在 BizTalk 管理主控台，以滑鼠右鍵按一下您 Wcf-basichttp 接收位置，然後選取**發佈至 API 管理**:  

    ![發佈功能表選項](../core/media/publish-to-api-management-option.png)
 
2. 設定您的 API 管理屬性： 

   1. **登入**到您 Azure 訂用帳戶中，選取**訂用帳戶**並**資源群組**具有 API 管理服務，，然後選取 您的服務。

   2. **WSDL 規格連結**會自動填入您的 WSDL 檔案。 取代**localhost** DNS 名稱或 IP 位址的 BizTalk Server。 

   3. 選取  **SOAP 傳遞**或是**SOAP 至 REST**:  
      * **SOAP 到 REST**： 從現有的 SOAP 式 web 服務建立 REST 架構 HTTP Api
      * **SOAP 傳遞**： 做為 SOAP API 的 proxy 

        API 可以藉由變更發佈這兩種方式**API URL 尾碼**，然後發佈一次使用不同的 API 類型。

   4. **API 名稱**會自動填入接收位置名稱。

   5. 選取  **API URL 尾碼**要使用的 API 取用者。 

      完成時，您的屬性看起來如下所示：  
      ![發佈至 API 視窗](../core/media/api-management-publish-window.png)


3. 選取 **發佈**。 成功時，接收位置會顯示為中的 API 管理中的服務[Azure 入口網站](https://portal.azure.com)。 

## <a name="do-more"></a>執行更多作業
Azure API 管理是功能強大服務所使用的許多 Azure 服務，包括邏輯應用程式。 API 管理包含許多功能，包括頻率限制和配額的人員存取您的 Api，快取，等等。 請參閱[什麼是 API 管理？](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)開始著手。

## <a name="see-also"></a>另請參閱
[設定 Feature Pack](configure-the-feature-pack.md)

---
title: "連接到使用 BizTalk Server 的 Azure API 管理 |Microsoft 文件"
description: "使用 BizTalk 功能組件 1 來連接到 API 管理中，從 BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: "2"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: d0c5e4cd2a0ebbd7108845ea15de468d0e0a5a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-azure-api-management"></a>連接到 Azure API 管理
您現在可以輕鬆地公開您的 SOAP 端點，透過從 BizTalk 應用程式開發介面管理。

## <a name="what-is-azure-api-management"></a>什麼是 Azure API 管理
用於 Azure API 管理周全的解決方案為 Api 發佈給外部和內部的客戶。 快速建立一致和裝載任何地方，現有的後端服務的現代應用程式開發介面閘道保護它們濫用與過度使用，並取得深入了解使用量和健全狀況。 此外，自動化並調整規模可幫助您的應用程式開發介面程式啟動並執行的開發人員入門訓練。 

請參閱[API 管理](https://azure.microsoft.com/en-us/services/api-management/)若要深入了解 API 管理。

## <a name="prerequisites"></a>必要條件
* 設定並設定[Azure API 管理](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)
* 建立[虛擬網路](https://docs.microsoft.com/en-us/azure/api-management/api-management-using-with-vnet)BizTalk 電腦與應用程式開發介面管理入口執行個體


1. 在 Azure 入口網站中，開啟您的 API 管理，然後選取**Api**從功能表：

    ![選取的 BizTalk 應用程式開發介面](../core/media/select-api-for-biztalk.png)
    
2. 選取的選項**WSDL**中新的應用程式開發介面 > 一節：

    ![選取 wsdl biztalk 應用程式開發介面](../core/media/select-wsdl-biztalk-api.png)
    
3. 若要連接至 BizTalk WSDL 的 API 管理，請將 URL 複製到您的 BizTalk 電腦到 SOAP 端點的完整 uri。 例如，複製`http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`:

    ![建立從 WSDL BizTalk 應用程式開發介面](../core/media/create-api-from-wsdl-biztalk.png)

4. 如果您想要使用，請選取**SOAP 傳遞**，或設定總**REST 的 SOAP**服務。
5. 輸入**名稱**您 API 的**描述**，而**API Url 尾碼**為您的服務。
6. 選取**建立**建立您的後端 SOAP 端點的通訊。

## <a name="see-also"></a>另請參閱
[設定 Feature Pack](configure-the-feature-pack.md)
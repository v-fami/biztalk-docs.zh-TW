---
title: SAP 配接器的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, overview
ms.assetid: 2d078b13-d41f-476f-bfb4-82be4d35a769
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3031bdf1317d96f64f1ea247c6f8cbf83e1688c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-sap-adapter"></a>SAP 配接器的概觀
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開為 WCF 服務的 SAP 系統。 配接器用戶端可以交換 SOAP 訊息的配接器，以執行 SAP 系統上的作業。 配接器會取用 WCF 訊息，並使適當地呼叫 SAP 系統執行的作業。 配接器傳回從 SAP 系統的回應傳回給用戶端的 SOAP 訊息格式。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]表面的中繼資料的 SAP 成品 (RFC，BAPI IDOC) 描述結構的 SOAP 訊息的 WSDL 格式。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料，並產生可使用的程式設計成品程式設計方案中。 如需有關[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 Unicode RFC 程式庫，librfc32u.dll，與 SAP 系統，除了使用其他支援的 Dll 進行通訊。 如需配接器需要的 SAP Dll 的完整清單，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南。 在一般安裝安裝指南 》\<安裝磁碟機：\>\Program Files\\[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。 您可以使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 SAP 系統通訊，以下列方式：  
  
-   開發 BizTalk 應用程式。 請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)如需詳細資訊。  
  
-   使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。 請參閱[開發 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。
  
-   使用 WCF 通道模型。 請參閱[開發 SAP 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。
  
## <a name="in-this-section"></a>本節內容  
  
-   [配接器如何連接到 SAP 系統？](https://msdn.microsoft.com/library/cc185540.aspx)  
  
-   [配接器介面的 SAP 中繼資料的運作方式](https://msdn.microsoft.com/library/dd788039.aspx)  
  
-   [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/dd788159.aspx)  
  
-   [配接器所支援的其他功能](https://msdn.microsoft.com/library/dd788022.aspx)  
  
## <a name="see-also"></a>請參閱  
 [了解 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)
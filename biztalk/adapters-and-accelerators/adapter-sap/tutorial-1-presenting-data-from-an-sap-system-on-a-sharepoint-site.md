---
title: "教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MOSS, creating an application in
- Microsoft Office SharePoint Server
- MOSS
- Microsoft Office SharePoint Server, creating an application in
ms.assetid: 6e31c365-446c-4fe1-8538-fa6c869eed63
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdc3ea5e41600aebcef1fda933735c418dec78c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site"></a>教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料
本教學課程提供詳細的指示使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft Office SharePoint Server，在 SharePoint 網站上呈現從 SAP 系統的商務資料。 若要示範如何使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]Office SharePoint Server，請考慮在任何企業中最常見的兩個實體： 客戶和銷售訂單。 在此範例中，建立應用程式中使用 Office SharePoint Server[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]執行下列動作：  
  
-   從搜尋字串為基礎的 SAP 系統中擷取客戶清單。  
  
-   從選取客戶 清單 和 顯示詳細資料的客戶。  
  
-   擷取所選客戶的銷售訂單。  
  
 若要從 SAP 系統中擷取客戶資料，此範例會使用 SD_RFC_CUSTOMER_GET RFC。 若要擷取特定客戶的銷售訂單的相關資訊，它會使用 BAPI_SALESORDER_GETLIST RFC。  
  
> [!NOTE]
>  某些版本的 SAP 系統公開 （expose) 而不是 SD_RFC_CUSTOMER_GET RFC_CUSTOMER_GET RFC。  
  
> [!NOTE]
>  本教學課程之前，確定您已安裝使用的所有必要條件[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]Office SharePoint server。 如需有關必要條件的詳細資訊，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南 》，通常安裝在 c: / Program 檔案/Microsoft  [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] /文件。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 將 SAP 成品發佈為 WCF 服務](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)  
  
-   [步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)  
  
-   [步驟 3： 建立 SharePoint 應用程式來擷取 SAP 資料](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)  
  
-   [步驟 4： 測試 SharePoint 應用程式](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md)  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器教學課程](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)
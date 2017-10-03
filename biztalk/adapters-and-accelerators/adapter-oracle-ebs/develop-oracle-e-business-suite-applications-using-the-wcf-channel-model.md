---
title: "開發 Oracle E-business Suite 應用程式使用 WCF 通道模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75bb6de1-e11a-4377-af13-e1cb954aaf3f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e99dfa0c69500b86fe086ce0daa81e3ffb62857d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-e-business-suite-applications-using-the-wcf-channel-model"></a>開發 Oracle E-business Suite 應用程式使用 WCF 通道模型
您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]直接透過使用 Oracle EBS 繫結建立通道執行個體傳送 XML 訊息。  
  
 使用 WCF 通道模型時，透過使用強型別類別與 WCF 服務模型會公開是通道模型會提供更細微的控制，透過執行 Oracle E-business suite 作業的方法的其中一項優點。 此控制項是來自事實，在 WCF 通道模型中，您直接控制您透過通道傳送訊息的內容。  
  
 在某些情況下，控制此額外層級可能有所助益。 例如，當您執行更新作業的資料表上使用 WCF 通道模型，您可以藉由略過您傳遞的訊息中的更新範本的資料行選擇性地更新目標資料列中的資料行。 所需的唯一資料行是那些與"nillable = false 」 在 WSDL 中。 所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中包含每個資料行中的資料表結構描述的強型別記錄參數。  
  
 本節中的主題說明如何在執行作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 WCF 通道模型。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [建立使用 Oracle E-business Suite 的通道](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-channel-using-oracle-e-business-suite.md)
  
-   [執行 Oracle E-business Suite 使用 WCF 通道模型中的介面資料表上的 insert 作業](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)  
  
-   [輪詢 Oracle E-business Suite 搭配 WCF 通道模型中使用 SELECT 陳述式](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)
  
## <a name="see-also"></a>另請參閱  
[開發 Oracle E-business Suite 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)
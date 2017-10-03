---
title: "中繼資料和 WCF 服務與 Oracle 資料庫的模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service model, metadata
- WCF client class
- WCF service contract
ms.assetid: b55cf4ed-c41a-4986-bbaf-88e80c32b01f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76933dba64e6e8bb75eb0394ab8e6eedd3fb7116
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-oracle-database"></a>中繼資料和 WCF 服務模型，與 Oracle 資料庫
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或者 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別，您的程式碼可以是：  
  
-   配接器 （WCF 用戶端類別） 上叫用作業  
  
-   接收來自配接器 （WCF 服務合約） 的作業  
  
 這些工具產生.NET 類別，代表目標作業 （以及支援訊息合約、 作業合約和資料合約） 的服務合約所公開的中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需協助了解這個產生的結構程式碼，請參閱 < 了解產生的用戶端程式碼 >，網址[http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365)。 本主題特別描述，svcutil.exe 會產生，但是其內容也適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。 如需有關如何產生 WCF 用戶端類別或目標作業的 WCF 服務合約以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[Oracle 資料庫產生 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)
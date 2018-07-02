---
title: 中繼資料和 WCF 服務模型與 Oracle 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service model, metadata
- WCF client class
- WCF service contract
ms.assetid: b55cf4ed-c41a-4986-bbaf-88e80c32b01f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b1c3eed2ab71282a50ccbb6709601aa69ca733
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973295"
---
# <a name="metadata-and-the-wcf-service-model-with-oracle-database"></a>中繼資料和 WCF 服務模型與 Oracle 資料庫
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別讓您的程式碼可以：  
  
- 配接器 （WCF 用戶端類別） 上叫用作業  
  
- 接收配接器 （WCF 服務合約） 中的作業  
  
  這些工具會產生代表服務合約為目標的作業 （以及支援的訊息合約、 作業合約和資料合約） 的.NET 類別所公開的中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需了解這個產生的結構的說明程式碼，請參閱 < 了解產生用戶端程式碼 >，網址[ http://go.microsoft.com/fwlink/?LinkId=98365 ](http://go.microsoft.com/fwlink/?LinkId=98365)。 本主題會具體描述，svcutil.exe 會產生，但其內容也會適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。 如需 svcutil.exe 之間的差異以及如何產生 WCF 用戶端類別或目標作業的 WCF 服務合約的相關資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[Oracle 資料庫產生 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型開發 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)
---
title: "中繼資料和 WCF 服務使用 Siebel 模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, metadata
- metadata, and the WCF service model
ms.assetid: 3aca1835-fb9e-4841-a920-078da0b3fe76
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed348c2ab183960b7af1383768259f67c4ca6270
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-siebel"></a>中繼資料和 Siebel 與 WCF 服務模型
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別，WCF 用戶端類別，透過其程式碼可以叫用作業上[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
 這些工具會使用配接器所公開的中繼資料來產生：  
  
-   表示目標作業的服務合約的註解式的.NET 介面。 這個介面會呼叫 WCF 服務合約。  
  
-   代表支援訊息合約、 作業合約和服務合約的資料合約的註解式的類別。  
  
-   WCF 用戶端類別，其方法可以用來叫用 WCF 服務合約所公開的服務方法 （作業）。  
  
 如需協助了解這個產生的結構程式碼，請參閱 < 了解產生的用戶端程式碼 >，網址[http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365)。 本主題特別描述，svcutil.exe 會產生，但是其內容也適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
 如需如何產生目標作業的 WCF 用戶端類別，以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
## <a name="see-also"></a>另請參閱  
 [開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)
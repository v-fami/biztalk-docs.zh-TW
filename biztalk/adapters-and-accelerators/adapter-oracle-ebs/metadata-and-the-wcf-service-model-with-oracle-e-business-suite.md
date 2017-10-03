---
title: "中繼資料和 WCF 服務模型與 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d3fcba-c72f-4ae9-82bd-abbfc2a0c2c4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cf87c0a579d1f0c0de590d78e559ead73be0cec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-oracle-e-business-suite"></a>中繼資料和 Oracle E-business Suite 之 WCF 服務模型
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 執行下列動作：  
  
-   產生服務合約，WCF 服務合約，透過此程式碼可以從配接器接收作業。 這個.NET 介面代表目標作業的服務合約。  
  
-   產生 proxy 類別，WCF 用戶端類別，透過此程式碼可以叫用的介面卡上的作業。  
  
-   代表支援訊息合約、 作業合約和服務合約的資料合約的註解式的類別。  
  
 如需協助了解這個產生的結構程式碼，請參閱 < 了解產生的用戶端程式碼 >，網址[http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365)。 本主題特別描述，svcutil.exe 會產生，但是其內容也適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
 如需有關如何產生 WCF 用戶端類別或目標作業的 WCF 服務合約以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[for Oracle E-business 產生 WCF 用戶端或 WCF 服務合約套件方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 服務模型來開發 Oracle E-business Suite 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
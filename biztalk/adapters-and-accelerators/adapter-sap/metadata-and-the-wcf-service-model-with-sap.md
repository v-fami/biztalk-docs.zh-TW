---
title: 中繼資料和 WCF 服務與 SAP 模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1900cf66-a0d0-46f4-896b-7f6de3b51875
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f06cd33c0776df70e5ff2554d355915908012abb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216774"
---
# <a name="metadata-and-the-wcf-service-model-with-sap"></a>中繼資料和 WCF 服務模型，與 SAP
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或者 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別，您的程式碼可以是：  
  
-   配接器 （WCF 用戶端類別） 上叫用作業  
  
-   接收來自配接器 （WCF 服務合約） 的作業  
  
 這些工具產生.NET 類別，代表目標作業 （以及支援訊息合約、 作業合約和資料合約） 的服務合約所公開的中繼資料從[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。 如需了解產生的程式碼的結構的說明，請參閱[了解產生的用戶端程式碼](https://msdn.microsoft.com/library/ms733881.aspx)。 本主題特別描述，svcutil.exe 會產生，但是其內容也適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。 如需如何產生 WCF 用戶端類別或 WCF 服務合約 （介面） 的目標作業以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[適用於 SAP 產生 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發使用 WCF 服務模型的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)
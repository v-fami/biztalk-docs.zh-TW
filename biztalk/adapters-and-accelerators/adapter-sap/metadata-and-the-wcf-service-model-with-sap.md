---
title: 中繼資料和 WCF 服務模型，使用 SAP |Microsoft Docs
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
ms.openlocfilehash: 8e4a3ca75470192f2237cf67c6ac0312b150b46a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972831"
---
# <a name="metadata-and-the-wcf-service-model-with-sap"></a>中繼資料和 WCF 服務模型，使用 SAP
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 來產生 proxy 類別讓您的程式碼可以：  
  
- 配接器 （WCF 用戶端類別） 上叫用作業  
  
- 接收配接器 （WCF 服務合約） 中的作業  
  
  這些工具會產生代表服務合約為目標的作業 （以及支援的訊息合約、 作業合約和資料合約） 的.NET 類別所公開的中繼資料從[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。 如需了解產生的程式碼結構的說明，請參閱 <<c0> [ 了解產生的用戶端程式碼](https://msdn.microsoft.com/library/ms733881.aspx)。 本主題會具體描述，svcutil.exe 會產生，但其內容也會適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。 如需如何產生 WCF 用戶端類別或 WCF 服務合約 （介面） 為目標的作業，以及 svcutil.exe 之間差異的詳細資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生適用於 SAP 的 WCF 用戶端或 WCF 服務合約方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發使用 WCF 服務模型的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)
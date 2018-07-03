---
title: 中繼資料和 SQL 配接器使用 WCF 服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4353ce67-f0e8-4f96-b1d9-95deeee7f3e6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfc6e490b2966a0b68d1a9c8669cf4601881743e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008223"
---
# <a name="metadata-and-the-wcf-service-model-with-the-sql-adapter"></a>中繼資料和 SQL 配接器使用 WCF 服務模型
在 WCF 服務模型中，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutile.exe) 執行下列動作：  
  
- 產生服務合約，WCF 服務合約，讓您的程式碼可以從配接器接收作業。 此.NET 介面代表目標作業的服務合約。  
  
- 產生 proxy 類別，WCF 用戶端類別，透過此程式碼可以叫用的介面卡上的作業。  
  
- 表示支援的訊息合約、 作業合約和服務合約的資料合約的註解的類別。  
  
  如需了解產生的程式碼結構的說明，請參閱 <<c0> [ 了解產生的用戶端程式碼](https://msdn.microsoft.com/library/ms733881.aspx)。 本主題會具體描述，svcutil.exe 會產生，但其內容也會適用於程式碼的程式碼，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。  
  
  如需 svcutil.exe 之間的差異以及如何產生 WCF 用戶端類別或目標作業的 WCF 服務合約的相關資訊和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
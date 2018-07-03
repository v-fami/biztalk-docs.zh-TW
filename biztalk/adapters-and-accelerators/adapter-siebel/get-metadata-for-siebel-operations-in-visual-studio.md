---
title: 取得 Visual Studio 中的 Siebel 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving for Siebel operations in Visual Studio
ms.assetid: 63643942-6497-4891-ad7d-34b1df9acbc1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b4a7b6ed8cfd678d725323d92de045d27e10085
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014535"
---
# <a name="get-metadata-for-siebel-operations-in-visual-studio"></a>取得 Visual Studio 中的 Siebel 作業的中繼資料
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]提供兩個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件。  
  
- [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]位於 BizTalk Server 專案。 您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生訊息結構描述 (Xsd) 的 BizTalk 解決方案中做為目標的作業。 如需有關如何使用 BizTalk Server 開發解決方案的詳細資訊，請參閱 <<c0> [ 使用 Siebel 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)。
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]用於非 BizTalk 的程式設計專案。 您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來開發使用 WCF 服務模型的方案時，產生 WCF 用戶端類別或 WCF 服務的回呼介面。 如需有關如何使用 WCF 服務模型開發解決方案的詳細資訊，請參閱 <<c0> [ 開發的 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)。  
  
  這兩種[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：  
  
- 提供的 Microsoft Windows 介面，您可以透過它瀏覽，然後搜尋您想要使用您的方案中的作業。  
  
- 正在擷取這些目標作業的配接器所公開的中繼資料。  
  
- 轉換該中繼資料，這會以 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的解決方案 （BizTalk 專案的 XSD 訊息結構描述或針對 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它新增至您的專案。  
  
  本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  

  
## <a name="see-also"></a>另請參閱  
[開發您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)
---
title: 取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87d7f731-cd0f-4970-a3cd-072f09312989
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f4a7b5d016adf1cc7fa8bb73772e1e5d7145520
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002071"
---
# <a name="get-metadata-for-oracle-e-business-suite-operations-in-visual-studio"></a>取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件：  
  
- [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]  
  
- [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]  
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]  
  
  配接器用戶端必須使用這些元件來連接到 Oracle E-business Suite，並接著產生在想要執行作業的中繼資料。 所有這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：  
  
- 提供的 Microsoft Windows 介面，您可以透過它瀏覽，然後搜尋您想要使用您的方案中的作業。  
  
- 正在擷取這些目標作業的配接器所公開的中繼資料。  
  
- 轉換該中繼資料，這會以 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的解決方案 （BizTalk 專案的 XSD 訊息結構描述或針對 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它新增至您的專案。  
  
  本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
> [!NOTE]
>  如果您已建立於特定版本的 Oracle E-business Suite 中，使用配接器的解決方案，而現在想要部署不同版本的 Oracle E-business Suite 解決方案您應該部署之前測試解決方案。 您可能會遇到問題，同時部署不同版本的 Oracle E-business Suite 解決方案，因為基礎構件的中繼資料可能會不同。 若要解決此問題，您應該重新產生在相同版本的 Oracle E-business Suite，您要部署解決方案中使用配接器的中繼資料。  
  

---
title: "取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d7f731-cd0f-4970-a3cd-072f09312989
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97ef4cc308979718f306958d0da1bb1eceaebaf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-for-oracle-e-business-suite-operations-in-visual-studio"></a>取得 Visual Studio 中的 Oracle E-business Suite 作業的中繼資料
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供三個[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可用來協助您開發解決方案使用配接器的元件：  
  
-   [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]  
  
-   [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]  
  
 配接器用戶端必須連接到 Oracle E-business Suite，使用這些元件，然後產生他們想要執行作業的中繼資料。 所有這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件簡化開發：  
  
-   提供的 Microsoft Windows 介面，您可以瀏覽和搜尋您想要使用您的方案中的作業。  
  
-   正在擷取這些目標作業的配接器所公開的中繼資料。  
  
-   轉換的中繼資料，這表示做為 Web 服務描述語言 (WSDL) 文件，配接器，成您可以使用您的方案 （BizTalk 專案的 XSD 訊息結構描述或 WCF 服務合約的.NET 物件表示法中的表單服務模型） 並將它加入至您的專案。  
  
 本節提供有關如何使用指示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
> [!NOTE]
>  如果您建立方案，在特定版本的 Oracle E-business Suite，使用配接器，而且現在想要部署在不同版本的 Oracle E-business Suite 方案然後您就應該測試方案後再進行部署。 您可能會面臨的問題時部署在不同版本的 Oracle E-business Suite 解決方案，因為基礎的成品的中繼資料可能會不同。 若要解決此問題，您應該重新產生在相同版本的 Oracle E-business Suite，您要部署方案中使用配接器的中繼資料。  
  

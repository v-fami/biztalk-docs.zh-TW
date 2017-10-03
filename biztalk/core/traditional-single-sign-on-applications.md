---
title: "傳統單一登入應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a49bdae7-215a-43fb-875e-f64abb37aef0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4396ecfab477fe1ae17b1abbb09ebf71c9bcb58c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="traditional-single-sign-on-applications"></a>傳統單一登入應用程式
「單一登入」(SSO) 程式設計架構包含用以對應應用程式與使用者的對應元件、用以尋查特定用途之認證的尋查元件，以及用以執行管理工作的管理元件。 此外，SSO 也包含票證介面，以便應用程式可發出和贖回票證。  
  
## <a name="mapping"></a>對應  
 對應是連結特定使用者與特定應用程式的程序。 您可以對應分支機構應用程式與使用 `ISSOMapping`、`ISSOMapper` 和 `ISSOMapper2` 的使用者。 有了 `ISSOMapping`，您就可以建立、刪除、啟用和停用對應。 有了 `ISSOMapper` 和 `ISSOMapper2`，您就可以取得和設定目前使用者的對應資料。  
  
## <a name="lookup"></a>查閱  
 「單一登入」程式設計介面的核心是尋查特定使用者之認證的能力。 您可以使用 `ISSOLookup1` 和 `ISSOLookup2` 查詢認證。 `ISSOLookup1` 可讓使用者擷取自己的外部認證。 相較之下，`ISSOLookup2` 也可讓您為本機分支機構應用程式尋查遠端使用者的認證。 前者為傳統「單一登入」應用程式的必要項目，而後者則在撰寫主控件初始化的「單一登入」應用程式時十分有用。  
  
## <a name="administration"></a>系統管理  
 您可以透過 `ISSOAdmin`、`ISSOAdmin2` 和 `ISSOConfigStore`，以程式設計的方式執行許多管理功能。 這類工作包括設定單一登入以及建立和描述要單一登入的應用程式。 您也可以使用 `ISSOConfigDB`、`ISSOConfigOM` 和 `ISSOConfigSS` 來建立及修改 SSO 資料庫。 最後，您可以使用 `ISSOPSAdmin` 來管理密碼同步功能。  
  
## <a name="communication-and-ticketing"></a>通訊和票證  
 您的應用程式極可能會發出訊息，以便您的使用者可以與遠端應用程式通訊。 若要更安全地與遠端應用程式通訊，您必須發出和贖回「單一登入」票證。 您也可以藉由程式設計的方式來發出和贖回票證。  
  
## <a name="see-also"></a>另請參閱  
 [單一登入應用程式](../core/single-sign-on-applications.md)
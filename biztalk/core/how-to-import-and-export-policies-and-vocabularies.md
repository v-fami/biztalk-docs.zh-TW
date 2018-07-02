---
title: 如何匯入和匯出原則和詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, exporting
- Rule Engine Deployment Wizard
- policies, importing
- vocabularies, exporting
- vocabularies, importing
ms.assetid: c427f686-5908-4f72-9e72-46a5497274ac
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bb235d126ca775cc8bd5a752388c948a2203e4b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968839"
---
# <a name="how-to-import-and-export-policies-and-vocabularies"></a>如何匯入和匯出原則和詞彙
您可以使用 [規則引擎部署精靈] 來匯入或匯出原則或詞彙。  

> [!NOTE]
>  原則或詞彙使用的所有詞彙都必須先行匯入，否則會發生錯誤。  

### <a name="to-import-or-export-a-policy-or-vocabulary"></a>若要匯入或匯出原則或詞彙  

1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則引擎部署精靈**。  

   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  

2. 在 歡迎使用 頁面上，按一下**下一步**。  

3. 上**部署工作**頁面上，選取**匯出原則/詞彙至檔案從資料庫**或是**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 [**下一步]**。  

4. 在 **原則存放區**頁面上，從下拉式清單中，選取可用的 SQL Server 電腦和資料庫，然後按一下 **下一步**。  

5. 在 **匯出原則/詞彙**頁面上，執行下列作業，然後按一下 **下一步**。  

   1.  選取 **原則**或是**詞彙**取決於您想要匯出/匯入。  

   2.  從**原則/詞彙**下拉式清單中，選取所需的原則/詞彙。  

   3.  按一下 **瀏覽**選取的定義檔。  

6. 檢閱伺服器、 資料庫及原則或詞彙的詳細資訊，，然後按**下一步**。  

7. 匯入或匯出完成後，按一下**下一步**。  

8. 檢閱匯入或匯出的完成狀態，然後按**完成**。

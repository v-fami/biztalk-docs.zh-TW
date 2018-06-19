---
title: 如何部署和解除部署原則和詞彙 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, policies
- policies, deploying
- deploying, vocabularies
- policies, undeploying
- vocabularies, deploying
ms.assetid: 9a7e3310-54b7-482c-8210-b4b11fde4c49
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef36df71459935b588f54c1dadc30ab02a7e722e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249566"
---
# <a name="how-to-deploy-and-undeploy-policies-and-vocabularies"></a>如何部署和解除部署原則與詞彙
您可以使用「規則引擎部署精靈」以部署或解除部署原則。  
  
 當您在「規則引擎部署精靈」中嘗試部署時，下拉式清單中只會顯示已發佈的原則版本。 當您嘗試解除部署時，只部署的原則版本會顯示在下拉式清單中。  
  
### <a name="to-deploy-or-undeploy-a-policy"></a>若要部署或解除部署原則  
  
1.  按一下**啟動**，指向  **Program Files**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **商務規則引擎部署精靈**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在**規則引擎部署精靈**歡迎頁面上，按一下 **下一步**。  
  
3.  選取 **部署原則**或**解除部署原則**，然後按一下 **下一步**。  
  
4.  從下拉式清單中，選取可用的 SQL Server 電腦和資料庫，然後**下一步**。  
  
    > [!NOTE]
    >  您只能將規則部署至所設定的規則存放資料庫。 嘗試部署至其他資料庫，將會發生錯誤。  
  
5.  從下拉式清單中，選取原則，然後**下一步**。  
  
    > [!NOTE]
    >  當您嘗試部署時，下拉式清單中只會顯示已發佈的原則版本。 當您嘗試解除部署時，只部署的原則版本會顯示在下拉式清單中。  
  
6.  檢閱伺服器、 資料庫和原則資訊，然後按一下**下一步**。  
  
7.  監看部署或解除部署的進度。 完成後，按一下**下一步**。  
  
8.  檢閱部署或解除部署，完成狀態，然後按一下**完成**。  
  
> [!NOTE]
>  您也可以部署或解除部署原則版本從 「 商務規則編輯器 」 中的以滑鼠右鍵按一下原則版本，然後按一下**部署**或**解除部署**。
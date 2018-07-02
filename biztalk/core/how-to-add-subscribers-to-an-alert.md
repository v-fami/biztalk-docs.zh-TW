---
title: 如何新增訂閱者至警示 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subscriptions, subscribers
- subscriptions
- managing [BAM], adding alert subscribers
ms.assetid: c76a117d-4516-4f48-995c-7e018dbba755
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0174d5f37bc34b6c882d82cb58192ce9f1d634d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972615"
---
# <a name="how-to-add-subscribers-to-an-alert"></a>如何新增訂閱者至警示
系統管理員可以使用**新增為訂用帳戶**命令，將訂閱者新增至指定的警示。  
  
### <a name="to-add-subscribers-to-an-alert"></a>新增訂閱者至警示  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。 按 ENTER 鍵。  
  
3. 輸入 `bm add-subscription -View:<view name> -Alert:<alert name> -AccountName:<account name> -Type: [ File | Email ][ -Email:<e-mail address> ]`。  
  
   > [!NOTE]
   >  *型別*指定 BAM 用來傳遞警示的傳遞方法。 如果您指定電子郵件的傳遞類型，則必須提供所傳遞警示的目標電子郵件地址。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
4. 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [如何從警示移除訂閱者](../core/how-to-remove-subscribers-from-an-alert.md)
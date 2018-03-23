---
title: 管理 BAM 定義檔案所需的使用者權限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb4fb73f-b783-4a04-9bd6-a135b3dd2655
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5e39c86eec0cf198a5b879cbc98d29321de71dc
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="required-user-rights-for-managing-bam-definition-files"></a>管理 BAM 定義檔案所需的使用者權限
任何角色中的使用者都可以建立、管理和檢視 BAM 定義檔案。 管理 BAM 定義檔案包括了部署和移除定義檔案，以及管理與定義檔案關聯的活動、檢視、警示和成品。  
  
 系統管理員必須維護適當的資產保護，例如使用適當的存取權限建立共用資料夾。 使用 Excel 的 BAM 增益集時，我們建議使用者將巨集安全性層級設定為高。  
  
 修改 BAM 定義檔不需要任何必要的使用者權限 (視存放定義檔案位置所設定的權限而定)。 對定義檔案所做的變更不會自動套用至 BAM 基礎結構。 若要套用變更，您必須使用 BAM 管理公用程式。  
  
 若要使用 BAM 管理公用程式，您必須是要套用 BAM 定義之電腦的系統管理員，或是 BizTalk Server 系統管理員群組的成員。  
  
> [!NOTE]
>  在支援 [使用者帳戶控制] (UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [何謂 BAM 定義？](../core/what-is-a-bam-definition.md)   
 [如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)
# Git ���� ����ϴ� ��ɾ� ����
���� ����ϴ� �⺻���� ��ɾ���� �����߽��ϴ�.

-- �ֱ� ������ : 2017-07-26

## ����� ����(�ʱ�ȭ) �ϱ�
```bash
git init    # ����� ����
```

## Ŀ���ϱ�
```bash
git add README.md    # Ŀ���� ���� �߰�
git status    # ���� stage ���¸� Ȯ��
git commit -m "init:README.md"    # �ζ��� Ŀ�� �޽��� �ۼ�
git log --deccorate=full --online --graph    # Ŀ�� �α� Ȯ��
```

## �귣ġ �����ϱ�
```bash
git checkout -b readme    # readme ��� �̸��� �귣ġ�� ������ ��, ������ �귣ġ�� üũ�ƿ�
```

## �����ϱ�
```bash
git merge readme --no-ff # readme �귣ġ�� ������ �ڰܿͼ� ������, fast-forword��� ��
```

## Fast Forward��?
```bash
Merge�� �귣ġ�� ����Ű�� �ִ� Ŀ���� �� �귣ġ�� ����Ű�� �� ���� '������ ������'Ŀ���̱� ������ master �귣ġ �����ʹ� �ֽ� Ŀ������ �̵��Ѵ�. �̷� Merge ����� 'Fast forward'��� �θ���. �ٽ� ���ؼ� A �귣ġ���� �ٸ� B �귣ġ�� Merge�� �� B�� A ������ Ŀ���� ����Ű�� ������ ���� A�� B�� Ŀ���� ����Ű�� �� ���̴�.
```

## branch �����ϱ�
```bash
������ ���� �ذ��ϰ� master �귣ġ�� �����ϰ� ���� �ٽ� ���ϴ� �귣ġ�� ���ư��� �Ѵ�. ������, ������ �ʿ���� �귣ġ�� �����Ѵ�. git branch ��ɿ� -d �ɼ��� �ְ� �귣ġ�� �����Ѵ�.

$ git branch -d [�ʿ���� �귣ġ �̸�]
Deleted branch [�ʿ���� �귣ġ �̸�] (was 3a0874c).
```

## 3-way merge
```bash
A - ���� - B �� ���Ͽ� A�� B �� ���� �κа� �ٸ� �κ��� �� ������ ���� ��, �� �κ��� �����Ǿ��ٰ� �Ǵ��� �� �ٸ� �κ��� �����´�. ������ ����, A,����,B ���� �ٸ� �����̸� A�� B���� �� �� ������ �Ǿ��ٰ� �Ǵ��� Conflict�� �Ǵ�. �׸��� ���� Ȯ���ϸ� �κк��� �Ǵ��� �������� ��� ���ο� ������ �����.

-2-way merge-
***
2-way merge�� �׳� ���ο� ������ �ƴ϶� ���� �ٸ� ������ ���� �κ��� ������ ������ Conflict�� �Ǵ�.
***

[ A ][ ���� ][ B ][ 2-way ][ 3-way ]
[ 1 ][   1  ][ 0 ][   ?   ][   0   ]
[ 2 ][   2  ][ 2 ][   2   ][   2   ]
[ 5 ][   3  ][ 6 ][   ?   ][   ?   ]
[ 0 ][   4  ][ 4 ][   ?   ][   0   ]

���� �ٸ� 2���� branch�� merge�� ��, �� ���� �ϳ��� ���� �ϳ��� ���� branch�� �ƴ϶��, �� branch commit�� ���� ����commit�� ã�� 3-way merge�� �����ϰ� �� ����� ���ο� commit�� ����� merge�� ������ branch�� �����Ͱ� �� Ŀ���� ����Ű���� �Ѵ�.

�̷��� ���� <Merge Commit>�̶�� �Ѵ�.

Merge Commit�� �̿��ϸ� commit history�� ����ϰ� ������ �� �ִ�.
```

## Rebase -> Merge�� �̿�����(��� Branch�� �ٸ� �۾��� �� ��)
```bash
��Ȳ�� ���� �ٸ�������, 
Merge�� ������ ��, rebase�� �������� �ʰ� �ܼ��� merge����� branch�� �����ϰԵǸ� History�� ����������, log�� ���� ���������.

������, rebase ��, merge�� �ϰԵǸ�, ���� ���̰� �ƴ� �ϳ��� ���̷� ����ϰ� ������ History�� log�� �� �� �ִ�.

History�� ����ϰ� �����ϴ� ���� �������� ���� �߿��ϴ�!
```

## �浹�� �Ͼ�� ��
```bash
�浹�� �Ͼ�� ��Ȳ�� Merge�� ��, ������ �귻ġ�� �������� ������ �ִ� ������ ���� �����Ǿ� ������ �ٸ��� ���� �� �߻��Ѵ�.
�浹�� �����ؼ� Merge�� �ߴܵǸ�, git status�� �浹�� �Ͼ ������ Ȯ���Ͽ�, �ش� ������ ������ ��, git add�� Staging area�� �����Ѵ��� �ٽ� commit�ϸ� Merge�� ����ȴ�.
```

## Clone vs Remote
```bash
Clone�� Ŭ���̾�Ʈ �� �ƹ��͵� ���� ��, ������ ������Ʈ�� �����޴� ��ɾ�μ�, ������� ������ �ٿ�ε� �ް� �ڵ����� initó���ȴ�.

Remote�� ���� ����Ҹ� ������ �� �ִ� ��ɾ�μ�, ��������Ҹ� ����Ͽ� ������ �� �ֵ��� ���ش�.
```

## Fork�� ���� ����
```bash
Fork�� �Ͽ� ����repository���� ����repository�� �����Ѵ�.
git clone ����repository�ּ�
�� ���� remote repository�� ���� ����ϰ� (��κ� �̸��� upstream�̶�� �Ѵ�.)
git remote add ����repository�ּ�
�� ���� ����repository�� ����Ѵ�.

1. ���� clone�ϱ�
2. ���� ����� remote�ϱ�
```

## Branch�� �����!
```bash
branch�� ����� ������ upstream�� �̿��Ͽ� �׻� �ֽ� ���·� �����ϴ°� ����.

git checkout master
git pull upstream

pull�� ���������� fetch�� �����Ͽ� �ֽ� ������ ������ ����, ���� ��ġ�� branch�� merge�ϴ� ������ �����Ѵ�.

branch�� ���� ������, �Ϲ����� branch �̸��� ����Ѵ�.(���� �׸� ����)

git checkout -b �̸� upstream/master # git checkout -b branchB branchA, branchA���� branchB��� ���ο� branch�� ����鼭 checkout�Ѵ�.
```

## upstream/master?
```bash
clone�� �ϰ��� git branch -a �� ������Ѻ��� ������ ���� ���´�.

* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master

���⼭ master�� ���� ������� branch�̰� remotes/origin/master�� origin ������ master branch �̸��̴�. 
�̷� ���� ����ϴ� ��Ȳ��

git diff origin/master..master
git diff remotes/origin/master..master

��� ����� �Ѵ�.

�� �ΰ��� ����� ���� ���� ��Ÿ����, 'remote master�� ���� master�� �ٸ����� �������� �����޶�'�� ���̴�.

remotes/origin/HEAD �� origin�� default branch�̸�, origin/master ��ſ� origin�̶�� �θ� �� �ְ� �Ѵ�.
```

## Branch name
```bash
�Ϲ������� "�̽�ID" of "�̽�ID" + "����(����)" �� ����Ͽ� �����Ѵ�.
```

## ���� ����Ʈ
```bash
http://www.popit.kr/%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4-git-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-pull-request-%EB%B3%B4%EB%82%B4%EA%B8%B0/
```

##
```bash
```